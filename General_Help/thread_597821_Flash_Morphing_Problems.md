---
title: "Flash Morphing Problems"
date: 2007-10-30
forum: General Help
---

### Post by Izek on 2007-10-30
When visiting sites such as youtube, or Sheezy, Linux cannot "morph" flash. Normally on sheezyART (IE: Windows) thumbnails come up as javaScripted images, but with linux, they come up as flash. (Below is an image of that problem)

[Link, since I'm on Xubuntu, and can't get the direct image](http://www.sheezyart.com/view/1506919/).

Now, a person has been having problems with another morphing issue. When on youtube, Linux doesn't morph the flash to go to full screen... however since the user was running compiz, they posted the problem on the compiz-fusion website... but in fact... it's a linux problem. I've reinstalled Xubuntu Gutsy, and added the flashplugin-nonfree via the Synaptics Package Manager to get Flash Player 9... and I have the same morphing problem (below, I made sure you see I'm not running compiz.) Please help.

[[IMG]http://img99.imageshack.us/img99/6383/200710301914211280x800snz5.th.png[/IMG]](http://img99.imageshack.us/img99/6383/200710301914211280x800snz5.png)

---

### Post by Izek on 2007-11-01
Although the youtube thing is fixed with flash player **9.0.48.0**... the SheezyART problem needs to be fixed. Why in the world does linux use flash on the thumbnails? Windows doesnt.

**Edit:** I've [already posted](http://www.sheezyart.com/forum/topic/92650/) this problem in SheezyART on *Oct 24th 2007*, but they haven't replied.

```
<script language="javascript">
		if (AC_FL_RunContent == 0) {
			alert("This page requires AC_RunActiveContent.js.");
		} else {
			AC_FL_RunContent(
				'codebase', 'http://download.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=9,0,0,0',
				'width', '315',
				'height', '228',
				'src', 'http://art3.sheezyart.com//flash/thumbs/thumb',
				'FlashVars', 'imageURL=http://art3.sheezyart.com/medium/149/1497809.jpg&imageEffect=blur&flashWidth=315&flashHeight=228',
				'quality', 'high',
				'pluginspage', 'http://www.macromedia.com/go/getflashplayer',
				'align', 'middle',
				'play', 'true',
				'loop', 'true',
				'scale', 'showall',
				'wmode', 'transparent',
				'devicefont', 'false',
				'id', 'thumb',
				'bgcolor', '#ffffff',
				'name', 'thumb',
				'menu', 'true',
				'allowFullScreen', 'false',
				'allowScriptAccess','sameDomain',
				'movie', 'http://art3.sheezyart.com//flash/thumbs/thumb',
				'salign', ''
				);
		}
	</script><noscript>
		<img src="http://art3.sheezyart.com/medium/149/1497809.jpg" alt="'Velvet Up Close' by iyeru" border=0 width="300" height="218"  />
	</noscript>
```

is the problematic code they use. [color=#FFFFFF]I could turn off JavaScript, but that would be an ugly way of doing it.[/color] **Edit:** I can't do that... because then I still can't full view images.

---

