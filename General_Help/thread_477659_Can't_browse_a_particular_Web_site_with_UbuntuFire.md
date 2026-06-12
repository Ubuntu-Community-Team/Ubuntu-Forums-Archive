---
title: "Can't browse a particular Web site with Ubuntu/Firefox"
date: 2007-06-18
forum: General Help
---

### Post by Jamie Jackson on 2007-06-18
I'm trying to browse a particular site, and all combinations of browsers (lynx, Firefox, IE, Opera) and OSs (Ubuntu, Win2k) can browse this site except for FF/Ubuntu.

This is the site in question:
[fatherhood.gov]("http://fatherhood.gov")

The error is: "The connection to the server was reset while the page was loading."

I don't know if FF/Ubuntu is just messing up, or whether it's alerting me to some obscure configuration problem of this site.

Can anyone help me diagnose?

Thanks,
Jamie

P.S. I'm using FF 2.0 and Ubuntu Feisty.
```

jamie@mercury:~$ firefox --version
Mozilla Firefox 2.0.0.4, Copyright (c) 1998 - 2007 mozilla.org
jamie@mercury:~$ uname -a
Linux mercury 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```

---

### Post by anaconda on 2007-06-18
hmm..

I didn't have any problems with the first link.  And I haven't got any "special" setting made..  Just Firefox in Ubuntu Dapper 
Maybe it was momentarily down?

---

### Post by Jamie Jackson on 2007-06-18
Thanks for the response, but no, this is a consistent problem with no change over the last few days.

I had a colleague try it, too and he had the same results as I did on his own Ubuntu(Feisty)/FF.

Maybe the difference between you and me is Dapper vs. Feisty?

Thanks for trying the links! Now I know that it's not necessarily Ubuntu/FF, but maybe just Feisty/FF that demonstrates the problem.

Thanks,
Jamie

---

### Post by Old *ix Geek on 2007-06-18
> **Jamie Jackson said:**
> These are the sites in question (and they're hosted by the same party):
[fatherhood.gov]("http://fatherhood.gov")
[acf.hhs.gov]("http://acf.hhs.gov")

The error is: "The connection to the server was reset while the page was loading."
Very odd.  I just tried both sites using SeaMonkey 1.1.1 (my normal browser) and Firefox 2.0.0.4.  The first link loaded just fine in SM, but FF yielded the same error message ("connection was reset") you got.  The second link wouldn't load in either SM or FF; in SM it's "address not found" and in FF it's "server not found."

For fun, I also tried Opera and Konqueror; those both loaded the first site just fine, but neither could find the second.  Are you quite sure that's the correct address?

FWIW, I'm using Feisty.

---

### Post by aktiwers on 2007-06-18
Cant connect to any of them.

---

### Post by Jamie Jackson on 2007-06-18
Apologies, the second link was plain wrong. I've edited it out of my first post. Let's forget about that (now non-existent) second link, please.

Do you have any idea why this site behaves strangely (i.e., not at all) in Feisty/FF?

Thanks,
Jamie

---

### Post by Feba on 2007-06-18
Address won't work on my Feisty FF. Strange indeed. If the page isn't too long, maybe it would be worth clicking VIEW, and VIEW SOURCE, and showing us what the source code looks like, so we could try to see what the problem is?

---

### Post by Gavin77 on 2007-06-18
Feisty/Firefox here.  Your link doesn't work but if you put www. in the address it loads ok.

---

### Post by anaconda on 2007-06-18
> **Feba said:**
> Address won't work on my Feisty FF. Strange indeed. If the page isn't too long, maybe it would be worth clicking VIEW, and VIEW SOURCE, and showing us what the source code looks like, so we could try to see what the problem is?

Here is the page source. (from: [http://fatherhood.gov](http://fatherhood.gov))

and as gavin said the second address works  if you add www. in front of it.. eg. [http://www.acf.hhs.gov/](http://www.acf.hhs.gov/)



	<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
	
	<title>Home - National Responsible Fatherhood Clearinghouse</title>
	
	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">

	<link href="/assets/styles/main.css" rel="stylesheet" type="text/css">
	<link rel="stylesheet" href="/assets/styles/image-box.css" media="screen" />
	<script language="JavaScript" src="/assets/scripts/slideshow.js" type="text/javascript"></script>
</head>

<body >
<table
 style="width: 100%;" border="0" cellpadding="0" cellspacing="0">
	<tbody>
		<tr>
			<td><!-- banner -->

				<table style="text-align: left; width: 100%;" border="0" cellpadding="0" cellspacing="0" id="banner">
					<tbody>	
						<tr>
							<td align="center" width="150"><!-- banner: left-->
								<a href="/index.cfm"><img src="/assets/images2/ui_nrfc_logo.gif" width="102" height="122" border="0" alt="NRFC Logo" title="National Responsible Fatherhood Clearinghouse"/></a>
							</td><!-- /banner: left -->
 
							<td><!-- banner: center -->
								<h1 title="National Responsible Fatherhood Clearinghouse">National Responsible Fatherhood Clearinghouse</h1>
							</td><!-- /banner: center -->

							<td width="30%"><!-- banner: right -->
								<table cellspacing="5" cellpadding="0" border="0" align="right">
									<form action="/search/results.cfm" method="get">
										 <tbody><tr>
										   <td valign="bottom" height="39" colspan="2"><div align="right"><a href="/search/search_tips.cfm">Search Tips</a> </div></td>
										   <td width="10%" valign="bottom" height="39"></td>
										 </tr>

										 <tr>
										   <td width="49%" height="30"><div align="right"><strong>Search NRFC: </strong></div></td>
										   <td width="41%" valign="top"><input name="criteria" type="text" /></td>
										   <td height="30"><input type="image" width="26" height="17" border="0" alt="Go! Button" src="/assets/images/top_gobt.gif"/></td>
										 </tr>
										 <tr>
										   <td height="26" colspan="2" class="navigation"><a href="/subscriptions/index.cfm">Email Updates</a>&nbsp;&nbsp;&nbsp;&nbsp;<a href="/sitemap.cfm">Site Map</a></div></td>

										   <td height="26"></td>
										 </tr>
									   </tbody>
									</form>
								</table>									
							</td><!-- /banner: right --->
						</tr>
					</tbody>
				</table>

			</td><!-- /banner -->
		</tr>

		<tr>
			<td><!-- trunk -->
				<table style="text-align: left; width: 100%;" border="0" cellpadding="0" cellspacing="0">
					<tbody>
						<tr valign="top">
							<td id="navbar_container_cell" width="162"><!-- navbar: main -->							
								
								<table width="100%" cellpadding="0" cellspacing="0">

									<tr>
										<td class="button"><a href="/index.cfm" alt="Home" title="NRFC Home">NRFC Home</a></td>
									</tr>	
									
									<tr>
										<td class="button"><a href="/father/index.cfm" alt="FatherFamily" title="Father and Family Resources">Father and Family Resources</a></td>
									</tr>	
									
									<tr>
										<td class="button"><a href="/grantees/index.cfm" alt="Grantee" title="Grantee Resources">Grantee Resources</a></td>

									</tr>	
									 
									<tr>
										<td class="button"><a href="/community/index.cfm" alt="Community" title="Community Partner Resources">Community Partner Resources</a></td>
									</tr>	
									
									<tr>
										<td class="button"><a href="/policymakers/index.cfm" alt="Policymaker" title="Policymaker Resources">Policymaker Resources</a></td>
									</tr>	
									
									<tr>
										<td class="button"><a href="/researchers/index.cfm" alt="Researcher" title="Researcher Resources">Researcher Resources</a></td>

									</tr>
									
									<tr>
										<td><p>&nbsp;</p></td>
									</tr>
									<tr>
										<td><img alt="Topics &amp; Tools" width="160" height="20" src="/assets/images2/ui_topics_hd.gif" id="topics-tools_header"/></td>
									</tr>
									<tr>
										<td class="button"><a href="/funding/index.cfm" alt="Funding" title="Funding">Funding</a></td>

									</tr>	
									<tr>
										<td class="button"><a href="/domestic_violence/index.cfm" alt="DomesticViolence" title="Domestic Violence">Domestic Violence</a></td>
									</tr>	
									<tr>
										<td class="button"><a href="/incarceration_reentry/index.cfm" alt="Reentry" title="Incarceration and Reentry">Incarceration and Reentry</a></td>
									</tr>	
									<tr>
										<td class="button"><a href="/mental_health/index.cfm" alt="MentalHealth" title="Mental Health/ Substance Abuse">Mental Health/ Substance Abuse</a></td>

									</tr>	
									<tr>
										<td class="button"><a href="/statistics/index.cfm" alt="Statistics" title="Statistics">Statistics</a></td>
									</tr>	
									<tr>
										<td class="button"><a href="/media.cfm" alt="Media Materials" title="Media Materials">Media Materials</a></td>
									</tr>
									<tr>
										<td class="button"><a href="http://basis.caliber.com/cwig/ws/library/docs/fatherhd/SearchForm" alt="LibaraySearch" title="Library Search">Library Search</a></td>

									</tr>
									<tr>
										<td class="button"><a href="/faq/index.cfm" alt="FAQ" title="Frequently Asked Questions">Frequently Asked Questions</a></td>
									</tr>
								</table>									
							</td><!-- /navbar: main -->
							<td valign="top" width="7"><!-- navbar: gutter --><img alt="" width="7"  height="8" src="/assets/images2/ui_curve.gif"/><br /><img alt="" width="7" height="770" src="/assets/images2/ui_left.gif"/>
							</td><!-- /navbar: gutter -->
							</td><!-- /navbar -->

							<td id="body"><!-- body -->
							
							
							<p class="breadcrumbs"></p>
							<h1 class="pageTitle">
	<br /><br />
	<span title="Welcome to the National Responsible Fatherhood Clearinghouse!">
		<img alt="" width="126" height="22" src="/assets/images2/header_welcome-to-the.gif" style="padding-right: 5px;"/><img 
			alt="" width="166" height="22" src="/assets/images2/header_national-fatherhood.gif" style="padding-right: 5px;" /><img 
			alt="" width="211" height="22" src="/assets/images2/header_fatherhood_clearinghouse.gif"/>
	</span>
</h1>
							


<p>The National Responsible Fatherhood Clearinghouse (NRFC) supports the <a href="http://www.acf.hhs.gov/">Administration for Children and Families'</a> <a href="http://www.acf.hhs.gov/programs/ofa/">Office of Family Assistance's (OFA)</a> efforts to assist States and communities to promote and support Responsible Fatherhood and Healthy Marriage.</p>  
	
<p>Primarily a tool for professionals operating Responsible Fatherhood programs,
the NRFC provides access to print and electronic publications, timely
information on fatherhood issues, and targeted resources that support
OFA-funded Responsible Fatherhood and Healthy Marriage grantees. The NRFC Web
site also provides essential information for other audiences interested in
fatherhood issues.</p>

<p>Feel free to take a look around the NRFC Web site by looking on the left for
resources relevant to who you are or in the "Topics and Tools" section in the
lower left for information relevant to a specific subject.</p>

<p>Don't forget to search our online library for information on Responsible
Fatherhood from statistical profiles, to program evaluations, to tips for how
to be a better father.</p>

<p>There is also an NRFC email newsletter that you can sign up for to receive free
email updates on what is new on fatherhood.gov!</p>


							

							</td><!-- /body -->
							
							
							<td width="185" id="sidebar_container_cell"><!-- sidebar -->
								
										
	
	
<!-- box -->
<div class="image-box">
	<div class="content">
		<div class="t"></div>
		<!-- box content -->


		<div align="center" style="padding-top: 10px;">
			<img alt="NewsAndUpdates" width="133" height="17" src="/assets/images2/ui_news_hd.gif">
		</div>
		<div align="center" style="padding-top: 10px;">
			<script type="text/javascript">	
				//debugger;
				//SET IMAGE PATHS. Expand or contract array as needed
				var fadeimages = new Array();
				
				
					fadeimages[0]=["/assets/images2/rotating/photo_01.jpg", "", ""];
				
					fadeimages[1]=["/assets/images2/rotating/photo_02.jpg", "", ""];
				
					fadeimages[2]=["/assets/images2/rotating/photo_03.jpg", "", ""];
				
					fadeimages[3]=["/assets/images2/rotating/photo_04.jpg", "", ""];
				
					fadeimages[4]=["/assets/images2/rotating/photo_05.jpg", "", ""];
				
					fadeimages[5]=["/assets/images2/rotating/photo_06.jpg", "", ""];
				
					fadeimages[6]=["/assets/images2/rotating/photo_07.jpg", "", ""];
				
					fadeimages[7]=["/assets/images2/rotating/photo_08.jpg", "", ""];
				
					fadeimages[8]=["/assets/images2/rotating/photo_09.jpg", "", ""];
				
					fadeimages[9]=["/assets/images2/rotating/photo_10.jpg", "", ""];
				
					fadeimages[10]=["/assets/images2/rotating/photo_11.jpg", "", ""];
				
				
				var slideshow_width=160; //SET IMAGE WIDTH
				var slideshow_height=125; //SET IMAGE HEIGHT
				var border_width = 0; // set border width
				var delay=10000; // set delay between slides
				var pause=0; //pause on mouseover? (1=yes,0=no)
			
			
				//new fadeshow(IMAGES_ARRAY_NAME, slideshow_width, slideshow_height, borderwidth, delay, pause (0=no, 1=yes), optionalRandomOrder ("R"=yes, remove parameter for no), altText )
				new fadeshow(fadeimages, slideshow_width, slideshow_height, border_width, delay, pause, null, 'Slideshow of fathers with children and families.');
			</script>
			<noscript>
				<img alt="Slideshow of fathers with children and families." 
					width="160" height="125" 
					src="/assets/images2/rotating/photo_01.jpg" 
					style="padding: 0px" />
			</noscript>	
			
		</div>
		<dl>

			<dt>Event Name:</dt>
			<dd>Training and Technical Assistance Conference for Healthy Marriage and Promoting Responsible Fatherhood Grantees</dd>
			
			<dt>Date:</dt>
			<dd>July 2007</dd>
			
			<dt>Sponsor:</dt>
			<dd>Administration for Children and Families</dd>

			
			<dt>For more information:</dt>
			<a href="mailto:info@fatherhood.gov">info@fatherhood.gov</a>		
		</dl>
	
		<!-- /box content -->
		
		<p></p>
	</div>
	<div class="b"><div></div></div>
</div>
<!-- /box -->



								
							</td><!-- /sidebar -->
						
						</tr>
					</tbody>
				</table>
			</td><!-- /trunk -->
		</tr>

		<tr>

			<td id="footer_containing_cell"><!-- footer 24457a -->

<hr />
<div align="center">



<a href="#skipfooternavigation"><img src="/assets/images/transparent1x1.gif" alt="Skip footer links to end of page" border="0"></a>	

<p>Download <a href="http://www.adobe.com/products/acrobat/readstep2.html">FREE Adobe Acrobat<sup>&reg;</sup> Reader&#8482;</a> to view PDF files located on this site.  
<a href="/exitdisclaimer.cfm"><img src="/assets/images/exitdisclaimer.gif" alt="Exit Disclaimer" width="87" height="13" border="0"></a></p>

<p> <a href="/contactus.cfm">Contact Us</a> | <a href="http://www.hhs.gov/Accessibility.html">Accessibility</a> | <a href="/privacy.cfm">Privacy Policy</a> | <a href="/disclaimer.cfm">Disclaimer</a> | <a href="http://www.acf.hhs.gov/acf_foia.html">Freedom of Information
Act</a> | <a href="http://www.whitehouse.gov/">White House</a> | <a href="http://www.usa.gov/">USA.gov</a></p>


<p><a href="/index.cfm">Home</a> | <a href="/aboutus.cfm">About Us</a> | <a href="/sitemap.cfm">Site Map</a> | <a href="/father/index.cfm">Father and Family Resources</a> | <a href="/grantees/index.cfm">Grantee Resources</a> | <a href="/community/index.cfm">Community Partner Resources</a> | <a href="/policymakers/index.cfm">Policymaker Resources</a> | <a href="/researchers/index.cfm">Researcher Resources</a> | <a href="/funding/index.cfm">Funding</a> | <a href="/domestic_violence/index.cfm">Domestic Violence</a> <br> <a href="/incarceration_reentry/index.cfm">Incarceration and Reentry</a> | <a href="/mental_health/index.cfm">Mental Health/ Substance Abuse</a> | <a href="/statistics/index.cfm">Statistics</a> | <a href="/media.cfm">Media Materials</a> | <a href="http://basis.caliber.com/cwig/ws/library/docs/fatherhd/SearchForm">Library Search</a> | <a href="/faq/index.cfm">Frequently Asked Questions</a></p>


</div>

<div class="hhs">

<table width="100%" cellspacing="5" cellpadding="5" align="center">
<tr>
<td class="a" width="45%" align="right"><a href="http://www.hhs.gov">U.S. Department of Health and Human Services</a><br>
Administration for Children and Families<br>Office of Family Assistance
</td>
<td width="8%" align="right" nowrap><img src="/assets/images/dhhs_logo.gif" width="51" height="57" border="0" alt="Department of Health and Human Services Logo"></td>
<td width="2%" nowrap><img src="/assets/images/blue_line.gif" width="3" height="80" border="0" alt=""></td>
<td width="45%" align="left">National Responsible Fatherhood Clearinghouse<br>

101 Lake Forest Boulevard, Suite 360<br />
Gaithersburg, MD 20877<br />
Toll-free: 1-877-4DAD411<br />
Fax: 301-948-4325<br />
Email: <a href="mailto:info@fatherhood.gov">info@fatherhood.gov</a></td>
</tr>
</table>


<p class="footer"><a name="skipfooternavigation">&nbsp;</a></p> 

</div>	

			</td><!-- footer -->

		</tr>
	</tbody>
</table>
</body>
</html>

---

### Post by joep on 2007-06-18
I'm using Swiftfox and it loads for me.

---

### Post by Feba on 2007-06-18
www. still does nothing. I wonder if it might be a problem with the way their webserver redirects traffic?

---

### Post by Jamie Jackson on 2007-06-18
> **Feba said:**
> Address won't work on my Feisty FF. Strange indeed. If the page isn't too long, maybe it would be worth clicking VIEW, and VIEW SOURCE, and showing us what the source code looks like, so we could try to see what the problem is?

Feba, thanks for the reply. However, I've got LiveHTTPHeaders running in FF, and I can see that FF never even performs the GET. It seems to be getting hung up before that point, so I think the page's HTML source is actually irrelevant.

Thanks,
Jamie

---

### Post by longlegs on 2007-06-18
Hi ,
I have a similar problem, where FF onces fails then fails forever with 'can't find server'
My only fix is to dump the entire contents of the cache folder including the cache map files. Then FF will try and succeed.
Good luck
longlegs

---

### Post by Mr. C. on 2007-06-18
Possible cause could be IPv6:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Or MTU mismatch, DNS problems, or the issue describe here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435)
[http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/](http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/)  <-- DEAD LINK
[http://marc.info/?l=postfix-users&m=115739945701551](http://marc.info/?l=postfix-users&m=115739945701551)

You'll need to perform these commands as root, so use "sudo" or equivalent to escalate your privileges.

MrC

---

### Post by Jamie Jackson on 2007-06-18
> **Mr. C. said:**
> Possible cause could be IPv6:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Or MTU mismatch, DNS problems, or the issue describe here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435)
[http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/](http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/)
[http://marc.info/?l=postfix-users&m=115739945701551](http://marc.info/?l=postfix-users&m=115739945701551)

MrC

I suspected IPv6 at the outset and disabled that in FF itself, which didn't work and led me to think that IPv6 wasn't the issue. However, maybe if I do it your way, it'll be okay.

I'll take a look at the links you sent.

Thanks,
Jamie

---

### Post by Old *ix Geek on 2007-06-18
> **Gavin77 said:**
> Feisty/Firefox here.  Your link doesn't work but if you put www. in the address it loads ok.

No, not for me.  That DOES make it work in SeaMonkey, Opera, and Konqueror, but NOT Firefox.  :confused:

---

### Post by Jamie Jackson on 2007-06-18
> **Mr. C. said:**
> Possible cause could be IPv6:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

Or MTU mismatch, DNS problems, or the issue describe here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=401435)
[http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/](http://inodes.org/blog/2006/09/06/tc...d-kernel-2617/)
[http://marc.info/?l=postfix-users&m=115739945701551](http://marc.info/?l=postfix-users&m=115739945701551)

MrC

Okay, I tried these things...

[LIST=1]
[*]It doesn't seem to be IPv6, as I blacklisted it as well as disabled the option in Firefox.
[*]It doesn't seem to be DNS, because it doesn't work when I hardcode in /etc/hosts
[*]It doesn't seem to be TCP Window Scaling, because changing it to the suggested values ("echo 4096 65536 65536 > /proc/sys/net/ipv4/tcp_rmem") doesn't work
[*]It doesn't seem like an MTU problem, since when I've had MTU problems, they weren't as localized as this. Further I lowered the MTU to what I figure is a conservative value (1200), but still no site. (sudo /sbin/ifconfig eth0 mtu 1200)
[/LIST]

Note, I did reboot after setting items 1 and 3, respectively.

What's next, file a bug report? With whom, Ubuntu? Mozilla?

Thanks,
Jamie

---

### Post by Mr. C. on 2007-06-19
See the third from the last post on the first page:

[http://ubuntuforums.org/showthread.php?t=445018&highlight=The+connection+to+the+server+was+reset+while+page+loading](http://ubuntuforums.org/showthread.php?t=445018&highlight=The+connection+to+the+server+was+reset+while+page+loading).

Perhaps that will help.
MrC

---

### Post by Jamie Jackson on 2007-06-19
That's so weird, when I searched for my thread this morning, I saw that post at the top of the list. I hadn't seen it before.

This hits the nail on the head!l The site works for me!

I guess I'll bug the host about their screwy proxy.

Thanks, Mr. C.!
Jamie

---

### Post by Mr. C. on 2007-06-19
Ah the web and its wonderful interoperability.

Glad its working.
MrC

---

### Post by Old *ix Geek on 2007-06-19
Yep, that solved it for me, too.

---

