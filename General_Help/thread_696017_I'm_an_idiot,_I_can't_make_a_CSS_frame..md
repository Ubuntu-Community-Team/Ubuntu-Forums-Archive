---
title: "I'm an idiot, I can't make a CSS frame."
date: 2008-02-13
forum: General Help
---

### Post by SZF2001 on 2008-02-13
Well, I've tried and tried. But I have no clue how to even start.

I grabbed KompoZer, which I heard will only work with frames if they are in this mysterious CSS coding. Fine, I thought, can't hurt to learn something new...

Well crap. I can't do it. No matter how many newb guides I try to follow, no matter what stuff I copy and paste, no matter what I try to even learn - thats right, instead of taking short cuts I tried to learn the stuff.

Please. Someone. There has to be SOMETHING out there that can explain all this in very very newb newb newb newb perspectives. Like, going back to kindergarten perspectives.

I SO SAD D:

---

### Post by OffAxis on 2008-02-13
try this out:
[http://w3schools.com/tags/tag_frame.asp]("http://w3schools.com/tags/tag_frame.asp")
and
[http://w3schools.com/css/default.asp]("http://w3schools.com/css/default.asp")

I'm not sure exactly what you need...

Are you SURE you need to use frames?

are you SURE you want to? :)

You might just be messing up the DTD tag in the heading...
It should be specific to the use of frames; for example:

[B]!DOCTYPE html PUBLIC
"-//W3C//DTD XHTML 1.0 Frameset//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd"[/B]

---

### Post by brennydoogles on 2008-02-13
> **SZF2001 said:**
>  ...in this mysterious CSS coding... 

lol. In order to write standards compliant code, it is best to use CSS to define all of the STYLE parts of your webpage, such as colors, font sizes, alignment, and anything having to do with background images, while using Xhtml to define the structure of your webpage (such as the following):
```

<html>
<head>
<style type="text/css">
<!--
body {
     background-color:blue;
     color:white;
}
p {
     background-color:white;
     color:blue;
}
-->
</style>
</head>
<body>
This will be white on a blue background
<p>Where this will be blue on a white background</p>
</body>
</html>

```

If you paste the code above into a file and give it a .html extension, you will see what I mean. Once you learn CSS, you will find that you can do so much more with web design, and you will also find that Microsoft Internet Explorer is the bane of web developers. I hope that helped!!

p.s.-- The links from the w3Schools website will be your best bet for learning the details of CSS, just give it a try!!

---

### Post by LaRoza on 2008-02-13
What do you want to do? Make a frame like window with CSS?

That is easy, you just position it, set the dimensions and set the overflow to scroll.

---

### Post by gnelson on 2008-02-13
> **LaRoza said:**
> What do you want to do? Make a frame like window with CSS?

That is easy, you just position it, set the dimensions and set the overflow to scroll.

I'll second that.  Don't bother with actual frames.  Use a DIV element with overflow:scroll; or overflow:auto;.

---

### Post by jken146 on 2008-02-13
> **LaRoza said:**
> What do you want to do? Make a frame like window with CSS?

That is easy, you just position it, set the dimensions and set the overflow to scroll.

Thirded.  Frames are evil.

---

### Post by OffAxis on 2008-02-13
> Thirded. Frames are evil.
lol.
I was trying to be subtle, but I like your direct approach.
Fourth-ed. Consider it a quorum.

---

### Post by nemilar on 2008-02-13
I'll join the pile-on.  Frames are terrible!

---

### Post by seventhc on 2008-02-13
I don't know what else to add other than fifth-ed don't use frames
and not to be a stickler, but the code above doesn't validate ;)

---

### Post by SZF2001 on 2008-02-14
Well, I guess I could attest to frames being evil... The last time I "designed" a website was in 99 with some out-dated-they-don't-make-anymore-program Adobe thing that I used on Windows 95.

I just need links to content staying on the left side (will be linking to various student pages) and the content in the right side. It's LIKE a frame, I guess, but I always did have trouble with them. So I'm not really up do date.

CSS is just for display? So I need to be using XHTML?

No wonder I've been so damn confused.

If anyone can help me in the process of my second paragraph, that'd be great. It's... *like* frames but it's *not*... I see it all the time on other sites...

Once I get this and RSS crap figured out I'll be the school superhero :D

---

### Post by seventhc on 2008-02-14
I think tables will do that. If you go to [http://w3schools.com/tags/tag_table.asp](http://w3schools.com/tags/tag_table.asp) if you scroll down some you'll see 
**Try-it-yourself-demos, **you can play around with them there, and then just use the code. There is a whole section each with it's own attributes so go through them all. After a while you have something good and have a better understanding how they work.

---

### Post by UK-Wobbie on 2008-02-14
I did not know you can ever make a frame in css coding lol
Only know that you can make a web frame in php coding and flash coding :)

---

### Post by seventhc on 2008-02-14
The link I gave is for tables in HTML.
You can do frames with HTML alone, but it's not the best thing to do.
IMO frames in general are bad, or as posted earlier, [COLOR=Red]evil[/COLOR].

---

### Post by UK-Wobbie on 2008-02-14
I say am the idot :lolflag:
l know a lot about CSS coding, but i did not look at what you put sorry :(
You can get a free tool what will help you do frame or anything in CSS coding!
It's called Simple CSS
[http://www.hostm.com/simplecss-download.m](http://www.hostm.com/simplecss-download.m)

---

### Post by brennydoogles on 2008-02-14
I don't really recommend building your site using tables.... that can be easily and more cleanly done using css. For example, I threw  [This Site]("http://weddings.brennyandangie.com/") together in an evening using valid Xhtml and CSS. If you would like to see the source code and a quick explanation of what it all means, let me know and I will happily post it up for you!!

---

### Post by seventhc on 2008-02-14
> **brennydoogles said:**
> I don't really recommend building your site using tables.... that can be easily and more cleanly done using css. For example, I threw  [This Site]("http://weddings.brennyandangie.com/") together in an evening using valid Xhtml and CSS. If you would like to see the source code and a quick explanation of what it all means, let me know and I will happily post it up for you!!
Could you please post that for me?
Thanks

---

### Post by brennydoogles on 2008-02-14
> **seventhc said:**
> Could you please post that for me?
Thanks

Sure!! I am going to take a few minutes to create a template html page into which you can just add content, as well as adding a bunch of comments to the CSS to make it more readily editable.

---

### Post by seventhc on 2008-02-14
Thank you very much. :)

---

### Post by Irony on 2008-02-14
This has some easy to follow CSS stuff;

[http://meyerweb.com/eric/css/](http://meyerweb.com/eric/css/)

---

### Post by brennydoogles on 2008-02-14
ok, here is the css:```
/* This is a CSS Comment */

/* The following section outlines the style for the body of the page. The background-color attribute will set the color around the main content box, while the color attribute sets text color for the body, unless specified more specifically. */
body {
	background-color:#CCD9BF;
	color:#000000;
	font-size:14pt;
	margin-left:20%;
	margin-right:20%;
	
}
/* This is the container div . You most likely don't need to play with much in here. */
div#container {
	width:100%;
	margin:0px;
	border:1px ridge #669933;
	line-height:150%;
}
/* This sets any attributes which are common to both the header and the footer. It just saves you from having to enter in the same information twice. */
div#header,div#footer {
	padding:0.5em;
	color:white;
	background-color:#669933;
	clear:left;
	border:1px ridge #669933;
	
}
/* This will set any attributes you want in the header that you don't want in the footer (or you want to be different in the footer) */
div#header {
	font-size:26pt;
	text-align:center;
}
/* Same thing... but with the footer */
div#footer {
	font-size:10pt;
	text-align:right;
}
/* This will set the attributes of the nav bar. note the float:left; attribute, that is what makes it not stack on top of the content div. */
div#left {
	float:left;
	width:180px;
	margin:0;
	padding:1em;
	background-color:#ffffff;
	height: 620px;
	text-align:center;
}
/* Here we set the attributes of the main content portion of the page. */
div#content {
	margin-left:190px;
	border-left:1px ridge #669933;
	padding:1em;
	padding-right:20px;
	height: 620px;
	background-color:#ffffff;
	overflow:scroll;
}
/* Here we set any attributes we want to be common to h1-h7. */
h1,h2,h3,h4,h5,h6,h7{
	text-align:center;
	color:#000000;
	font-weight:bold;
}
/* Here we get more specific about our h1-h7, declaring a size for each. If you wanted, you could even use these sections to have each h1 be a different color from each h2 across your whole site (not sure why you would want to do that....) */
h1 {
	font-size:26pt;
}
h2 {
	font-size:24pt;
}
h3 {
	font-size:22pt;
}
h4 {
	font-size:20pt;
}
h5 {
	font-size:18pt;
}
h6 {
	font-size:16pt;
}
h7 {
	font-size:14pt;
}
/* Here we set the attributes for the paragraph tags If you would like your paragraphs to all be intendented for you, just add in the line text-indent:10px; */
p {
	text-align: left;
	font-size:16pt;
}
/* This attribute would make the first letter of every paragraph red and size 20 font.
p:first-letter {
	font-size:20pt;
	color:red;
}
*/
/* These set the properties for all of your link states. */
a {
	color:#669933;
}
a:visited {
	color:#0F88F3;
}
a:hover {
	color:#2E577D;
}
a:active {
	color:#FFFFFF;
}

```

And Here is the HTML template: ```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

	<html xmlns="http://www.w3.org/1999/xhtml">

	<head>

		<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
		<title>Title</title>
		<meta name="author" content="YOUR NAME" />
		<!-- The entry below is a link to your stylesheet... edit it to reflect the name of your stylesheet -->
		<link rel="stylesheet" type="text/css" href="stylesheet.css" />
	</head>
	<body>

	</body>
		<div id="container">
			<div id="header">
				Here you may add your header content.     
			</div>
			<div id="left">
				Here you may add a nav bar on the left side.
			</div>
			<div id="content">
				Add your main Page content Here!
			</div>
			<div id="footer">
				Add your Footer Content Here
			</div>
		</div>
	</body>
</html>
```

I have also uploaded both as a tar.gz file to make life easier. Have fun!!

---

### Post by seventhc on 2008-02-14
Great, thanks :)
One question, there is a grey section that seperates left side from the right side. Does that close as content gets wider?

---

### Post by seventhc on 2008-02-14
> **Irony said:**
> This has some easy to follow CSS stuff;

[http://meyerweb.com/eric/css/](http://meyerweb.com/eric/css/)
Thats a good link :)

---

### Post by SZF2001 on 2008-02-14
I'm looking into your answers real quick - just opened other pages in tabs and will inspect them.

But tell me - this page was made with KompoZer, and the content seems to be what I'm looking for; links on the left side and content on the right.

[http://www.charlescooke.me.uk/web/ugs01.htm](http://www.charlescooke.me.uk/web/ugs01.htm)

Is it built with tables or CSS or wha...?

---

