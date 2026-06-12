---
title: "Problem accessing one website (alislam.org)"
date: 2007-09-13
forum: General Help
---

### Post by mirzmaster on 2007-09-13
Hello, all.

I'm having trouble accessing one particular website on the web, [http://www.alislam.org/](http://www.alislam.org/).  The problem in accessing it is a particularly strange one.  Where the site fails to load, it seems only part of the HTML content is being downloaded and then the page load stalls.  The throbber in Firefox continues throbbing, but the site will not finish loading.

I should add that I first encountered problems in trying to load the site only a few weeks ago (I don't recall exactly when).  I don't recall the problem coinciding with a particular update or anything.

Here is the behaviour I am seeing across various platforms and browsers:

[LIST]
[*]Feisty, Firefox 2.0.0.6 **(my default setup)** -- [COLOR="Red"]Site fails to load in its entirely.[/COLOR]
[*]Feisty, Firefox 2.0.0.5 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Firefox 1.5.0.12 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Seamonkey 1.1.3 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Galeon 2.0.2 -- [COLOR="Red"]Site fails to load in its entirety.[/COLOR]
[*]Feisty, Lynx 2.8.5rel.1 -- [COLOR="Red"]Site fails to load in its entirety[/COLOR] (despite the face that Lynx shows HTTP 1.1/200).
[*]Dapper, Firefox 1.5.0.? -- [COLOR="Green"]Loads successfully![/COLOR]
[*]Feisty, Windows XP VMWare Guest, Firefox 2.0.0.6 -- [COLOR="Green"]Loads successfully![/COLOR]
[*]Windows XP, Firefox 2.0.0.6 -- [COLOR="Green"]Loads successfully![/COLOR]
[/LIST]

Now, from the above, the problem appears to be isolated to browsers running natively in Feisty.  I've had another friend verify that he too is experiencing the problem.  He is running Feisty as well.

Can anyone verify that they are experiencing the same problem, or speculate on why this problem may be occurring?

By the way, this may be of interest... the partial HTML source of the site that does manage to come down.  You can see that it is clearly incomplete, and thus nothing actually renders:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"><html xmlns="http://www.w3.org/1999/xhtml">






<head>
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
<title>Al Islam Online - Ahmadiyya Muslim Community</title>
<meta name="Description" content="Al Islam - Official website of Ahmadiyya Muslim Community - a religious organization, international in its scope, with branches in over 189 countries.  This is the most dynamic denomination of Islam in modern history, with worldwide membership exceeding tens of millions." />
<meta name="Keywords" content="ahmadiyya, ahmadiyya movement, worldwide ahmadiyya movement,ahmadiyya movement in islam, islam ahmadiyyat , ahmadiyyat, ahmadi, mirza masroor ahmad, islamic organization, sects in islam , khilafat, prophet muhammad" />
<Meta http-equiv="expires" content="Never">
<Meta name="robots" content="All">
<META name="revisit-after" content="7 Days">
<Meta name="distribution" content="Global”>
<Meta name="classification" content="Religion">

<link rel="search" href="opensearchdescription.xml" type="application/opensearchdescription+xml" title="alislam.org" />

<link href="sitewide-styles/homepage-styles.css" rel="stylesheet" type="text/css" />
<link href="dynamic-homepage-content/jalsa/jalsa.css" rel="stylesheet" type="text/css" />



<link href="dynamic-homepage-content/primary/active/ramadhan/primary.css" rel="stylesheet" type="text/css" />
<script language="javascript" src="sitewide-scripts/scroll/ts_files/scroll.js"></script>
<script src="sitewide-scripts/jumpmenu.js" language="javascript" type="text/javascript"></script>

</head>

<body id="page-body" leftmargin="0" topmargin="0" marginwidth="0" marginheight="0">

<div id="youtube-layer" style="background: #000000; position:absolute; top:0; left:0; right:0; bottom:0; z-index:10002; filter: alpha(opacity=60); -moz-opacity: 0.6; opacity:0.6; height:100%; width:100%; display: none;"></div>
<div id="youtube-promo" style="position: fixed; background: #ffffff; left: 40%; top: 50%;  margin-top: -50px; margin-left: -100px;  z-index:999999; display: none;">
 <table cellspacing="0" cellpadding="4">
 <tr bacground="green"><td background="green" align="right" v-align="middle">

 <a href="javascript:closeyoutube();"><font-face="areal">close</font></a>&nbsp;</td></tr>
 <tr><td>
</td>
</tr></table>
 </div>

<div id="overDiv" style="position:absolute; visibility:hidden; z-index:1000;"></div>
<div id="container-page">
  <div id="container-branding" class="clearfix">
    <div id="container-bismillah">
      <p id="bismillah" class="replace" title="In the Name of Allah, The Most Gracious, Ever Merciful"><span class="empty"></span><em><span class="accessible">In the Name of Allah, The Most Gracious, Ever Merciful.</span></em></p>
    </div>
    <div id="container-logo">
      <h1 id="logo" class="replace" title="Al Islam - The official website of the Ahmadiyya Muslim Community"><span class="empty"></span><span class="accessible">Al Islam</span></h1>

    </div>
    <div id="container-tagline">
      <p id="tagline" class="replace" title="Love for All, Hatred for None"><span class="empty"></span><span class="accessible">Love for All, Hatred for None.</span></p>
    </div>
  </div>
  <div id="container-body" class="clearfix">
    <div id="container-sidebar" class="clearfix">
        <!-- Site Search -->

      <div id="site-search">
		<FORM method=GET action=http://www.google.com/u/alislam>
           <h2><label for="sitesearch">Search Al Islam</label></h2>
           <input name="q" type="text" id="sitesearch" size="16" maxlength="255" />
           <button id="sitesearch-button" name="sa" type="submit">Search</button>
        </form>
      </div>

	<!-- Site Search End -->
      <!-- Site Navigation -->
      <div id="container-nav">
        <h2 class="accessible">Browse Al Islam</h2>
        <ul id="nav-main">
          <li id="active"><span id="current">Home</span></li>
          <li><a href="/library/islam.html">Islam</a></li>

          <li><a href="/introduction/index.html">Ahmadiyyat</a></li>
          <li><a href="/library/">Library</a></li>
          <li><a href="http://store.alislam.org/" target="_blank">Online Store</a></li>
        </ul>
      </div>
      <!-- Language -->


			<div id="nav-language"><form action="language.php" method="POST">

          <h2>Language:</h2>
          <ul class="clearfix">
            <li id="button-urdu" title="Urdu"><a href="/urdu/">Urdu</a></li>
            <li id="button-arabic" title="Arabic"><a href="http://www.islamahmadiyya.net/" target="_blank">Arabic</a></li>
          </ul>
          <select name="language" onchange="MM_jumpMenu('parent',this,0)">

            <option selected="selected">- Other -</option>
            <option value="/chinese/Chinese.htm">Chinese</option>
            <option value="/spanish/">Español</option>
            <option value="/french/">Français</option>
			<option value="/japan/">Japanese</option>
            <option value="/malayalam/">Malayalam</option>

            <option value="/russian/">Russian</option>
            <option value="/swahili/">Swahili</option>
            <option value="/turkish/">T&uuml;rk&ccedil;e</option>
			<option value="/affiliated-websites.php">-- Countries --</option>
          </select>
          
```

---

### Post by angryfirelord on 2007-09-13
I'm not getting anything. I think it's a bandwidth issue and the server is timing out.

---

### Post by mirzmaster on 2007-09-13
> **angryfirelord said:**
> I'm not getting anything. I think it's a bandwidth issue and the server is timing out.

I'ts most definitely **not** a server load/bandwidth issue.  I just tried the site again in the Windows XP VM and it's working flawlessly.

---

### Post by Gwelmi on 2007-10-02
Hi,

I think i am experiencing the exact same problem.

The sites that do not load, entirely or partially, are [www.salesforce.com](www.salesforce.com), [www.netsec.ca](www.netsec.ca), ...

I tried alislam.org and it is not working either.

There is a story behind it : i moved office last week, and so as my machine. At the former location, everything worked fine. The internet connection was going throu a linksys router BEFSR81. 
Now at the new location i am having this problem, and internet conection goes throu linksys router RV042.
I checked all the settings differences i could think of between both routers, but no luck.

I tried to disable IPv6, no success.

The same website are working perfectly under any browser from MacOS X and WinXP, throu the same connection and cable.

Any pointer, thought, suggestion greatly appreciated.

G.-

---

### Post by neptune on 2007-10-02
I have the same setup as the original poster and I'm getting the same problem loading that website.

However, the other websites mentioned by the previous poster are working fine for me.

Weird :confused:

---

### Post by zvacet on 2007-10-03
I don´t have any problems to load that websites.I tryed with Firefox 2.0.0.6 and Opera 9.23.

---

### Post by dcstar on 2007-10-03
The problem seems the same as another issue where a >512MB RAM install has problems.

I cannot load this site with my default 2GB RAM Ubuntu 6.10, but when I boot my system only using 500MB RAM (Grub boot option: "mem-500M"), I can load this site.

I don't know if it is a kernel or Java (or whatever) issue, but now two totally different web sites seem to have the same problem:

[http://ubuntuforums.org/showthread.php?t=556256](http://ubuntuforums.org/showthread.php?t=556256)

---

### Post by Gwelmi on 2007-10-05
> **dcstar said:**
> The problem seems the same as another issue where a >512MB RAM install has problems.

I cannot load this site with my default 2GB RAM Ubuntu 6.10, but when I boot my system only using 500MB RAM (Grub boot option: "mem-500M"), I can load this site.

I don't know if it is a kernel or Java (or whatever) issue, but now two totally different web sites seem to have the same problem:

[http://ubuntuforums.org/showthread.php?t=556256](http://ubuntuforums.org/showthread.php?t=556256)

Thanks dcstar ! 
you are totally right, same thing happens for me with [https://uobcyberbanking.com](https://uobcyberbanking.com).
I submit my result to the poll that [samphan]("http://ubuntuforums.org/member.php?u=256208") created [here]("http://ubuntuforums.org/showthread.php?t=560222").

This is very weird indeed. Do you know if the bug have been reported already ?

Cheers.
G.-

---

### Post by dcstar on 2007-10-06
> **Gwelmi said:**
> 

This is very weird indeed. Do you know if the bug have been reported already ?

Cheers.
G.-

No idea, but I would recommend waiting a couple of weeks until the Ubuntu 7.10 version is released to see if it still is a problem, if so then it should be reported - if not then we can all upgrade to overcome the issue.

The boot string "fix" of adding "mem=500M" will still allow people to access these sites - and someone may want to experiment by upping the "mem" number until it is broken again, it may add some insight to when the problem is triggered off at a certain amount of available memory.

---

### Post by sonmez on 2007-10-12
Hello,

I am having accessing [www.citicards.com](www.citicards.com) It is the same problem.
I am running Fiesty and am planning to upgrade very soon.

---

### Post by reza81 on 2007-10-12
These acces problems are not a FF issue! It works fine here... 
It's a server &OR bandwide problem ...

try angain later!

---

