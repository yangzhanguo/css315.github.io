<!DOCTYPE html>
<html>
<head>
        <meta charset="utf-8" />
        <title>
        </title>
        <style>
            html,body { height: 100%; margin: 0; }
            #box { padding: 10px;}
            #changediv{width: 100px; height: 100px; border: 4px solid #393129; background: #fff;margin-top: 20px;}
            #btn1 { width: 100px; height: 40px; border: none; padding:0; background: red; color: #fff; cursor: pointer; outline: none;}
            #alertbox{ position: absolute; left: 450px; width: 300px; height: 200px; border:20px solid #9c949c; background: #fff; font-size: 14px; text-align: center;font-family:"微软雅黑"; display: none; z-index: 2; top: 200px;} 
            .color a {width: 34px; height: 30px; line-height: 30px; display:inline-block; margin-right:5px; text-decoration: none; font-size: 12px; color: #fff;}
            .px a { width:34px; height: 30px; background:#efefef; border: 1px solid #c0c0c0; margin-right:5px; display: inline-block; background: #fff; line-height: 30px; color:#808080; text-decoration: none; font-size: 12px;} 
            #c_red { background:red; border: 1px solid red;}
            #c_yellow { background: #efbd00;border: 1pxsolid #efbd00; }
            #c_blue { background: blue;border: 1px solid blue;} 
            #alertbox input { margin-right: 5px; border: none; background: #002952; color: #fff; width: 60px; height: 30px; cursor: pointer; outline: none;} 
            #bg {position:absolute; left: 0; top: 0; height: 100%; width: 100%; background: #000;opacity: 0.4; display: none;} 
			#alertbox a:hover { color: #000; border:1px solid #000;}
        </style>
</head>
    
    <body>
        <div id="box">
                       请为下面的DIV设置样式：
            <input id="btn1" type="button" value="点击设置" />
            <div id="changediv">
            </div>
            <div id="alertbox">
                <p class="color">
                    请选择背景颜色：
                    <a id="c_red" href="javascript:">
                        红
                    </a>
                    <a id="c_yellow" href="javascript:">
                        黄
                    </a>
                    <a id="c_blue" href="javascript:">
                        蓝
                    </a>
                </p>
                <p class="px">
                    请选择宽（px）：
                    <a id="w_200" href="javascript:">
                        200
                    </a>
                    <a id="w_300" href="javascript:">
                        300
                    </a>
                    <a id="w_400" href="javascript:">
                        400
                    </a>
                </p>
                <p class="px">
                    请选择高（px）：
                    <a id="h_200" href="javascript:">
                        200
                    </a>
                    <a id="h_300" href="javascript:">
                        300
                    </a>
                    <a id="h_400" href="javascript:">
                        400
                    </a>
                </p>
                <input id="huifu" type="button" value="恢复" />
                <input id="queding" type="button" value="确定" />
            </div>
        </div>
        <div id="bg">
        </div>
        <script>
            window.onload = function() {
                var aAbtn = $$("alertbox", "a");
                var ochangeDiv = $("changediv");
                for (var i = 0; i < aAbtn.length; i++) {
                    aAbtn[i].onclick = function() {
                        var id = this.id;
                        var firstL = id.substr(0, 1);
                        var value = id.substring(id.indexOf('_') + 1, id.length);
                        switch (firstL) {
                        case "c":
                            ochangeDiv.style.background = value;
                        case "w":
                            ochangeDiv.style.width = value + "px";
                        case "h":
                            ochangeDiv.style.height = value + "px";
                        };
                    };
                };

                $("btn1").onclick = function() {
                    $("alertbox").style.display = $("bg").style.display = "block";
                };

                /*
				   给每个啊A标签都加一个onclcik事件显得很臃肿
				   
				var ochangeDiv=$("changediv");
				$("c_red").onclick=function(){
					ochangeDiv.style.background="red";
				};
				$("c_yellow").onclick=function(){
					ochangeDiv.style.background="yellow";
				};
				$("c_blue").onclick=function(){
					ochangeDiv.style.background="blue";
				};
				
				$("w_200").onclick=function(){
					ochangeDiv.style.width="200px";
				};
				$("w_300").onclick=function(){
					ochangeDiv.style.width="300px";
				};
				$("w_400").onclick=function(){
					ochangeDiv.style.width="400px";
				};
				
				$("h_200").onclick=function(){
					ochangeDiv.style.height="200px";
				};
				$("h_300").onclick=function(){
					ochangeDiv.style.height="300px";
				};
				$("h_400").onclick=function(){
					ochangeDiv.style.height="400px";
				};
				*/
                $("huifu").onclick = function() {
                    ochangeDiv.style.height = "100px";
                    ochangeDiv.style.width = "100px";
                    ochangeDiv.style.background = "#fff";
                };

                $("queding").onclick = function() {
                    $("alertbox").style.display = $("bg").style.display = "none";
                };

            };

            function $(id) {
                return document.getElementById(id);
            };

            function $$(id, tagName) {
                return document.getElementById(id).getElementsByTagName(tagName);
            };
        </script>
    </body>
</html>