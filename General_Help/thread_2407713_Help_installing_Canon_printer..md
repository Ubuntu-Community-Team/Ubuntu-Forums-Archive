---
title: "Help installing Canon printer."
date: 2018-12-07
forum: General Help
---

### Post by Kris_Uguisu on 2018-12-07
Hello,

I have been trying to set up a Canon Satera LBP6030 printer on my computer. I will say at the start I have no idea what I am doing. 

So far I have downloaded the driver and installer? from [https://cweb.canon.jp/cgi-bin/download/select-software.cgi](https://cweb.canon.jp/cgi-bin/download/select-software.cgi) 

I have downloaded both of these. I have tried clicking on the files in the Debian and RPM folders, which open up the software centre to install things, but then cause the software centre to experience internal errors.

The previous link is all in Japanese, as with the general help manual [https://oip.manual.canon/USRMA-0280-zz-SS-jaJP/frame_htmls/home.html](https://oip.manual.canon/USRMA-0280-zz-SS-jaJP/frame_htmls/home.html)

In the folder that the downloaded drivers came in there is help for installing the drivers, also in Japanese. [https://oip.manual.canon/USRMA-0592-zz-DR-jaJP/contents/dlu-inst-flow.html#lcn_install_flow](https://oip.manual.canon/USRMA-0592-zz-DR-jaJP/contents/dlu-inst-flow.html#lcn_install_flow)

From what I can gather, it seems to be saying that to install using the installer you should type the following in the terminal.

&#31471;&#26411;&#65288;&#12479;&#12540;&#12511;&#12490;&#12523;&#65289;&#12363;&#12425;&#12473;&#12540;&#12497;&#12540;&#12518;&#12540;&#12470;&#12540;&#27177;&#38480;&#12391;&#12289;&#12452;&#12531;&#12473;&#12488;&#12540;&#12521;&#12434;&#23455;&#34892;

 			&#29694;&#22312;&#12487;&#12451;&#12524;&#12463;&#12488;&#12522;&#12364;&#12289;install.sh&#12434;&#26684;&#32013;&#12375;&#12390;&#12356;&#12427;&#12487;&#12451;&#12524;&#12463;&#12488;&#12522;&#12391;&#12354;&#12427;&#22580;&#21512;&#12398;&#20363;&#12434;&#27425;&#12395;&#31034;&#12375;&#12414;&#12377;&#12290;

 			sudo&#12467;&#12510;&#12531;&#12489;&#12434;&#20351;&#29992;&#12377;&#12427;&#22580;&#21512;

 			 				[TABLE="class: table_general"]
 					 						[TR]
 							[TD="class: col_0 row_0 table_general_col_0 table_general_row_0, colspan: 1"] 								$ sudo ./install.sh
 							[/TD]
 						[/TR]
 					 				[/TABLE]
 			
 			su&#12467;&#12510;&#12531;&#12489;&#12434;&#20351;&#29992;&#12377;&#12427;&#22580;&#21512;

 			 				[TABLE="class: table_general"]
 					 						[TR]
 							[TD="class: col_0 row_0 table_general_col_0 table_general_row_0, colspan: 1"] 								$ su
 								# ./install.sh

[/TD]
[/TR]
[/TABLE]


I have tried this but no luck. That is about as far as my Japanese and Linux expertise runs. To be honest, I understand words like `debian` about as much as I understand words like `&#31471;&#26411;`, so I am really hoping someone can give me a simple step by step on how to set this printer up. Computer is running Ubuntu 14.04 LTS with a 64-bit OS.

---

### Post by him610 on 2018-12-08
> Computer is running Ubuntu 14.04 LTS with a 64-bit OS.
You may need to update your system to LTS 18.04. From what I have seen at this Canon support webpage, 
[https://www.canon.ie/support/consumer_products/products/printers/laser/i-sensys_lbp6030.aspx?type=drivers&language=&os=Linux%20(64-bit)]("https://www.canon.ie/support/consumer_products/products/printers/laser/i-sensys_lbp6030.aspx?type=drivers&language=&os=Linux%20(64-bit)") , it appears that this is a fairly new printer. Some of the files are dated October 2018. There seem to be instructions in English on the support site also.

---

### Post by Kris_Uguisu on 2018-12-09
Thank you for your reply. I managed to get it to work. (^_^)

---

