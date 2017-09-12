# css3-Gradual-opening
css3集合JQ实现鼠标点击图片渐变翻开切换焦点
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>jQuery鼠标点击图片透明渐变翻开切换焦点图</title>
<link rel="stylesheet" type="text/css" href="css/style.css" />
<style>
	body{background-color:#F5F3F3 }
	h1{
		text-align:center;
		font-size:18px;
	}
	.container{
		background:#FF9; 
		width:420px; 
		height:300px; 
		margin:0px auto; 
		cursor:pointer; 
		overflow:hidden; 
		box-shadow:6px 4px 5px hsla(0,0%,59%,.2); 
		-webkit-box-shadow:6px 4px 5px hsla(0,0%,59%,.2); 
	}
	.container img{
		background:#FFF;
		display:block;
		width:400px;
		height:280px;
		padding:10px;
		float:left;	
		-webkit-transition:0.7s;
		-moz-transition:0.7s;
		-o-transition:0.7s;
	}
	.zoom{
		position:absolute;
		-moz-transform:translate(-150px,-120px);
		-webkit-transform:scale(1.1) translate(-150px,-120px) skew(0deg,0deg);
		-ms-transform:scale(1.1) translate(-150px,-120px) skew(15deg,-30deg);
		-o-transform:scale(1.1) translate(-150px,-120px) skew(15deg,-30deg);
	}
	.name{
		background:#FFF;
		width:220px;
		height:30px;
		margin:15px auto;
		cursor:pointer;
		box-shadow:2px 2px 5px #969696;/*opera或ie9*/ 
		-webkit-border-radius:20px;
		-moz-border-radius:20px;
		border-radius:20px;
	}
	
	.name p{
		font:bold 24px Verdana, Geneva, sans-serif;
		text-align:center;
		line-height:30px;
		color:#FFF;
		background:#333;
		-webkit-border-radius:20px;
		-moz-border-radius:20px;
		border-radius:20px;
	}
</style>
<script src="http://www.jq22.com/jquery/jquery-1.10.2.js"></script>
<script type="text/javascript">
$(function(){   
	var interval;
	$(".container img").click(function cover(){
		$(this).addClass("zoom").fadeOut(700,append);		
		function append(){
			$(this).removeClass("zoom").appendTo(".container").show();
			var name = $(".container").children("img").first().attr("alt");
			$(".name p").text("No "+name);
		}	
	  
	})
	
	function auto(){
		var play = $(".container").children("img").first();
		play.addClass("zoom").fadeOut(700,append);		
		function append(){
			$(this).removeClass("zoom").appendTo(".container").show();
			var name = $(this).parent().children("img").first().attr("alt");
			$(".name p").text("No "+name);
		}
		interval = setTimeout(auto,5000);
	}
	
	$(".container img").hover(function(){
			stopPlay();
	},function(){
			interval = setTimeout(auto,5000);
	})
	
	function stopPlay(){
		clearTimeout(interval);
	}
	auto();
					
})
</script>
</head>
<body>
<h1>jQuery鼠标点击图片透明渐变翻开切换焦点图</h1>

  <!--效果html开始-->
  <div class="container" style="margin-top:100px"> 
      <img src="images/a1.png" alt="1" /> 
      <img src="images/a2.png" alt="2" /> 
      <img src="images/a3.png" alt="3" /> 
      <img src="images/a4.png" alt="4" /> 
      <img src="images/a5.png" alt="5" /> 
  </div>
  <div class="name">
    <p>No 1</p>
  </div>

</body>
</html>
