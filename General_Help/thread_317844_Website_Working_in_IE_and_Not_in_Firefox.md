---
title: "Website Working in IE and Not in Firefox"
date: 2006-12-13
forum: General Help
---

### Post by gerowen on 2006-12-13
This is not related to my operating system, so I didn't really know where else to put it, if this is the wrong place, I apologize.  Anyway, here's my dilemma.

This isn't really a huge deal, but I was helping Ash' Leigh(my wife) make this web page for her technology class.  I showed her the basics of making a table and how to use NVU, and most of it was done by her.  The index page passes the w3c standards test and I've looked it over a thousand times and can't figure this out.  I didn't have IE installed on my Linux box at the time so I couldn't double check it, but it looked fine in Firefox.  However when I started asking friends to take a peek at it and make sure it looked ok, the ones using IE said the alignment was off, and sure enough when I checked it on my laptop it was.  This isn't a very big page, but could someone look at the code and tell me why it doesn't appear right in IE?  It's affected in versions 6 and 7 and if there's a workaround to make it look right in both browsers that would be nice.

[Firefox Screenshot](http://i2.photobucket.com/albums/y45/dudeman41465/Computer%20Screenshots/ashlaipageinff.jpg)

[Internet Explorer Screenshot](http://i2.photobucket.com/albums/y45/dudeman41465/Computer%20Screenshots/ashlaipageinie.jpg)

Code:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
  <meta content="text/html; charset=ISO-8859-1"
 http-equiv="content-type">
  <title>Welcome</title>
</head>
<body
 style="background-image: url(blank%20Community%20bulletin%20board.gif); background-position: center; background-attachment: fixed;">
<table
 style="width: 90%; text-align: left; margin-left: auto; margin-right: auto;"
 border="0" cellpadding="0" cellspacing="0">
  <tbody>
    <tr>
      <td style="text-align: center;"><img
 style="width: 534px; height: 163px;" alt="Title Banner"
 title="Title Banner" src="Title%20of%20home%20page.PNG"><br>
      </td>
    </tr>
  </tbody>
</table>
<br>
<table
 style="width: 792px; text-align: left; margin-left: auto; margin-right: auto;"
 border="0" cellpadding="2" cellspacing="0">
  <tbody>
    <tr>
      <td style="text-align: center;"><a
 href="KTIP.html"><img
 style="border: 0px solid ; width: 239px; height: 46px;"
 alt="KTIP Lesson Plan" title="KTIP Lesson Plan"
 src="KTIP.png"></a></td>
      <td style="text-align: center;"><a
 href="Downloads.htm"><img
 style="border: 0px solid ; width: 239px; height: 46px;"
 alt="Downloadables" title="Downloadables"
 src="Downloads.PNG"></a></td>
      <td style="text-align: center;"><a
 href="digibook.html"><img
 style="border: 0px solid ; width: 232px; height: 46px;"
 alt="Digital Storybook" title="Digital Storybook"
 src="digital%20story.png"></a></td>
    </tr>
  </tbody>
</table>
<table
 style="width: 792px; text-align: left; margin-left: auto; margin-right: auto;"
 border="0" cellpadding="2" cellspacing="0">
  <tbody>
    <tr>
      <td style="text-align: center;"><a
 href="bboard.html"><img
 style="border: 0px solid ; width: 239px; height: 46px;"
 alt="Bulletin Board" title="Bulletin Board"
 src="bulletinboard.jpg"></a></td>
      <td style="text-align: center;"><a
 href="Power%20Point.html"><img src="power%20point.png"
 title="PowerPoint" alt="PowerPoint"
 style="border: 0px solid ; width: 239px; height: 46px;"></a></td>
    </tr>
  </tbody>
</table>
<table
 style="width: 792px; text-align: left; margin-left: auto; margin-right: auto;"
 border="0" cellpadding="0" cellspacing="0">
  <tbody>
    <tr>
      <td><br>
      <big><span style="font-family: Times New Roman;">I'm
Ash' Leigh
Adams and this website is dedicated to work I
have done this year in my "Integrating Technology" class at Morehead
State University. &nbsp;I am a junior at Morehead; my major is
Early
Education (P-5). &nbsp;My component is Social studies, and I like
to
take classes in Art History. &nbsp;I enjoy reading, mainly modern
fiction but historical works also; I also enjoy plays and museums/art
galleries. &nbsp;I am recently married, my husband works with
computers
so I am trying to learn more about programming and web design.
&nbsp;I
hope to graduate from Morehead State in May of 2009, and start work
somewhere in Kentucky.</span></big></td>
    </tr>
    <tr>
      <td style="text-align: center;"><small><small><br>
Created and developed by:<br>
Ash' Leigh Adams (<a title="E-mail me!"
 href="mailto:ashlaiadams@gmail.com">ashlaiadams@gmail.com</a>)<br>
Last update: December 6th 2006<br>
Background from: <a
 href="http://www.wkki.net/K94%20Cares%20About%20the%20Commuity.htm">http://www.wkki.net/K94%20Cares%20About%20the%20Commuity.htm</a><br>
Any other art is either original or clipart<br>
This site is best viewed with <a title="Get Firefox NOW!!"
 href="http://www.getfirefox.com">Mozilla Firefox</a>
at
1024x768 resolution<br>
      <a href="http://validator.w3.org/check?uri=referer"><img
 style="width: 69px; height: 26px;"
 src="http://www.w3.org/Icons/valid-html401"
 alt="Valid HTML 4.01 Transitional"></a> </small></small></td>
    </tr>
  </tbody>
</table>
<br>
</body>
</html>

```

---

### Post by ciscosurfer on 2006-12-13
I'm not trying to put you off, but maybe this question would be better suited in an HTML/CSS forum.  Or at least the [Programming subforum]("http://ubuntuforums.org/forumdisplay.php?f=39") here on the Forums.

---

### Post by Sef on 2006-12-13
> The index page passes the w3c standards test and I've looked it over a thousand times and can't figure this out.

IE doest not follow w3c standards.  Microsoft follows its own standards.

---

