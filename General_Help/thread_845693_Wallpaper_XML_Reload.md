---
title: "Wallpaper XML Reload?"
date: 2008-06-30
forum: General Help
---

### Post by lotrkev on 2008-06-30
Ok, I have created an XML Document that changes the desktop wallpaper automatically. I have tried it and it has worked great, except for the fact that after it runs through all of the pictures, it won't restart at the beginning. What is the XML command to reload itself or restart the pics?

Here is the XML Doc:
----------------------------------------------------------------------------
<background>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Parq.jpg</file>
	</static>	
	<transition>
		<duration>2.0</duration>
		<from>/home/kevin/Pictures/Desktops/Parq.jpg</from>
		<to>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</to>
	</transition>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</file>
	</static>
	<transition>
		<duration>2.0</duration>
		<from>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</from>
		<to>/home/kevin/Pictures/Desktops/Red Planet.jpg</to>
	</transition>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Red Planet.jpg</file>
	</static>
	<transition>
		<duration>2.0</duration>
		<from>/home/kevin/Pictures/Desktops/Red Planet.jpg</from>
		<to>/home/kevin/Pictures/Desktops/Waterfire.jpg</to>
	</transition>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Waterfire.jpg</file>
	</static>
</background>

-------------------------------------------------------------------------------

---

### Post by Christian Marini on 2009-06-29
I know this thread is a year old, but I have the same question and this is the closest I've come to an answer with google. I was also wondering if anyone knows where I could find more info on xml wallpaper commands and what-not.

Thanks

---

### Post by Axel-P on 2009-08-07
I did something easy with a similar program and it worked, I put the  while (truth). It should look like this: ```
<background>
while (truth){
<static>
<duration>20.0</duration>
<file>/home/kevin/Pictures/Desktops/Parq.jpg</file>
</static>
<transition>
<duration>2.0</duration>
<from>/home/kevin/Pictures/Desktops/Parq.jpg</from>
<to>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</to>
</transition>
<static>
<duration>20.0</duration>
<file>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</file>
</static>
<transition>
<duration>2.0</duration>
<from>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</from>
<to>/home/kevin/Pictures/Desktops/Red Planet.jpg</to>
</transition>
<static>
<duration>20.0</duration>
<file>/home/kevin/Pictures/Desktops/Red Planet.jpg</file>
</static>
<transition>
<duration>2.0</duration>
<from>/home/kevin/Pictures/Desktops/Red Planet.jpg</from>
<to>/home/kevin/Pictures/Desktops/Waterfire.jpg</to>
</transition>
<static>
<duration>20.0</duration>
<file>/home/kevin/Pictures/Desktops/Waterfire.jpg</file>
</static>
}
</background>
```

---

### Post by tylerannosaurus on 2010-02-09
I've made xml files to create a background slideshow, but they won't change...I used the same format as mentioned above.

I can see the changes when I go to appearance settings, but not on my actual background.

Any ideas? I'm using Karmic.

---

### Post by harmck on 2010-02-10
> **lotrkev said:**
> Ok, I have created an XML Document that changes the desktop wallpaper automatically. I have tried it and it has worked great, except for the fact that after it runs through all of the pictures, it won't restart at the beginning. What is the XML command to reload itself or restart the pics?

Here is the XML Doc:
----------------------------------------------------------------------------
<background>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Parq.jpg</file>
	</static>	
	<transition>
		<duration>2.0</duration>
		<from>/home/kevin/Pictures/Desktops/Parq.jpg</from>
		<to>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</to>
	</transition>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</file>
	</static>
	<transition>
		<duration>2.0</duration>
		<from>/home/kevin/Pictures/Desktops/Night of Ubuntu.jpg</from>
		<to>/home/kevin/Pictures/Desktops/Red Planet.jpg</to>
	</transition>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Red Planet.jpg</file>
	</static>
	<transition>
		<duration>2.0</duration>
		<from>/home/kevin/Pictures/Desktops/Red Planet.jpg</from>
		<to>/home/kevin/Pictures/Desktops/Waterfire.jpg</to>
	</transition>
	<static>
		<duration>20.0</duration>
		<file>/home/kevin/Pictures/Desktops/Waterfire.jpg</file>
	</static>
</background>

-------------------------------------------------------------------------------

I used the format of the XML without a problem.

I think you must make the last entry the same as your first, this I believe will create the loop. Adding the while (truth) code to the XML, while (no pun intended) I haven't tried it, I think it is not needed. I could be wrong. 

I copied the 'cosmos' example, I'm using Karmic also, and I appear to have created a slideshow. 

Here is my XML if it makes a difference. 

```
<background>
  <starttime>
    <year>2010</year>
    <month>01</month>
    <day>01</day>
    <hour>00</hour>
    <minute>00</minute>
    <second>00</second>
  </starttime>
<!-- This animation will start at midnight. -->
  <static>
    <duration>1795.0</duration>
    <file>/home/harry/Pictures/Wallpapers/harry/glendalough-1.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/harry/Pictures/Wallpapers/harry/glendalough-1.png</from>
    <to>/home/harry/Pictures/Wallpapers/harry/glendalough-2.png</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/home/harry/Pictures/Wallpapers/harry/glendalough-2.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/harry/Pictures/Wallpapers/harry/glendalough-2.png</from>
    <to>/home/harry/Pictures/Wallpapers/harry/glendalough-3.png</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/home/harry/Pictures/Wallpapers/harry/glendalough-3.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/harry/Pictures/Wallpapers/harry/glendalough-3.png</from>
    <to>/home/harry/Pictures/Wallpapers/harry/malta_wave.jpg</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/home/harry/Pictures/Wallpapers/harry/malta_wave.jpg</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/harry/Pictures/Wallpapers/harry/malta_wave.jpg</from>
    <to>/home/harry/Pictures/Wallpapers/harry/melbourne_stkilda_marina.png</to>
  </transition>
  <static>
    <duration>1795.0</duration>
    <file>/home/harry/Pictures/Wallpapers/harry/melbourne_stkilda_marina.png</file>
  </static>
  <transition>
    <duration>5.0</duration>
    <from>/home/harry/Pictures/Wallpapers/harry/melbourne_stkilda_marina.png</from>
    <to>/home/harry/Pictures/Wallpapers/harry/glendalough-1.png</to>
  </transition>
</background>
```

---

### Post by tylerannosaurus on 2010-02-10
Yeah, I tried every which way...the odd thing is that the cosmos one doesn't seem to work anymore either. Same thing: it shows the new background when I go to the appearance menu but not on my actual desktop. Maybe a screenshot will show you what I mean.

[IMG]http://www.flickr.com/photos/44263804@N03/4346950956/sizes/o/[/IMG]

Note the wallpaper where my cursor is.

In case the picture doesn't show up like it doesn't for me: [http://www.flickr.com/photos/44263804@N03/4346950956/sizes/o/]("http://www.flickr.com/photos/44263804@N03/4346950956/sizes/o/")

---

### Post by Ghost|BTFH on 2010-03-03
<static>
<duration>20.0</duration>
<file>/home/kevin/Pictures/Desktops/Waterfire.jpg</file>
</static>
</background>

Needs to have a transition added to it back to the beginning. ie:

<static>
<duration>20.0</duration>
<file>/home/kevin/Pictures/Desktops/Waterfire.jpg</file>
</static>
<transition>
<duration>2.0</duration>
<from>/home/kevin/Pictures/Desktops/Waterfire.jpg</from>
<to>/home/kevin/Pictures/Desktops/Parq.jpg</to>
</transition>
</background>

Cheers,
Ghost|BTFH

---

