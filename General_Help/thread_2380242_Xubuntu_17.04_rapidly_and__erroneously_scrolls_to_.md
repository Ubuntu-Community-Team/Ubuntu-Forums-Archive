---
title: "Xubuntu 17.04 rapidly and  erroneously scrolls to bottom of page"
date: 2017-12-14
forum: General Help
---

### Post by Ralph L on 2017-12-14
Very often, but randomly, when I click on the vertical slide, Xubuntu 17.04 will rapidly scroll to the bottom of page.  Usually I am just clicking on the slide to move it up and down so I can get the page where I want it.  This happens frequently and is very annoying.  Does anyone else have this problem or am I the only one.  I am running Clearlooks Phenix under Setting>Appearance>Style, and Daloa under Settings>Window Manager>Style.  I also am using the Synaptics/Synclient driver to control the touchpad.  I notice this behavior mostly on Firefox (both pre-version 57 and with version 57), but I think it happens other places (can't be sure).

Thanks for any help.

---

### Post by vasa1 on 2017-12-14
I think it has to do with changes in GTK3 scrollbars. You could try legacy scrolling. See [https://askubuntu.com/questions/774200/how-to-fix-the-scrollbar-new-behaviour-in-firefox](https://askubuntu.com/questions/774200/how-to-fix-the-scrollbar-new-behaviour-in-firefox) even though it's for Firefox, it works in most other gtk3 apps as well.

---

### Post by Ralph L on 2017-12-15
Vasa1,
Thanks for the suggestion.  I will give it a try and get back here if it doesn't work.

---

### Post by Ralph L on 2017-12-15
Vas1,
I tried your suggestion.  It doesn't fix the problem.  Vertical slider still, randomly and frequently, quickly scrolls to the bottom of page, when I click on it.  

Any other thoughts??

---

### Post by vasa1 on 2017-12-15
Maybe try another mouse?

---

### Post by Ralph L on 2018-02-15
I am running Xubuntu 17.04 and have an annoying little problem.  If I click on the scrollbar, not on the slider, the slider moves down a page as it should.  However, if I don't very quickly release the button, the slider very quickly repeats the "scroll a page" command until it it at the bottom (or top) of the window.  Does anybody know how to slow this super rapid repeating so that the "scroll a page" is useful?  There must be some parameter somewhere that sets the delay, before the command is repeated.

Any help appreciated........

Thanks,
Ralph

---

### Post by vasa1 on 2018-02-15
Not to your point, but 17.04 is EOL. You won't get security updates and possibly other updates.

Here's a [link dealing with GNOME scrolling]("https://blog.gtk.org/2017/10/11/a-scrolling-primer/").

It would help if you mention the applications involved. On 16.04, scrolling in only _some_ applications is as you describe.

---

### Post by vasa1 on 2018-02-16
Merged threads.

---

### Post by Ralph L on 2018-02-16
Vasa1

The problem is mainly with Firefox.  (Note that I am using synclient, since it provides options that I need to get my giant clickpad working for me--a thumb clicker/ palm dragger.)  I tried several apps and they all work a little differently from one another, but Firefox is the big problem.  I am running Firefox 57.0.1.  I went to about:config and tried mousewheel.acceleration.factor, mousewheel.acceleration.start, and mousewheel.min_line_scroll_amount.  None of them made any difference at all.  But maybe they should have no affect, since I am using a touchpad with no middle button emulation and clicking on the slider/slider trough.  With google I could find reference to no about:config parameters that related to clicking on the firefox scrollbar slider, or slider trough.  Do you know of any??????

I did make some minimal progress by setting synclient EmulateMidButtonTime=500, even though I have no middle button defined in synclient.  This slowed the time between left button click on the slider or trough and any action.  It gave me time to release the left click button before the slider took off for the bottom/top of the trough.  

You mentioned that xubuntu 17.04 is end of life.  I hope to switch to 18.04, but I have heard bad reports about Wayland--that it doesn't have the options to get my clickpad working the way I want.  Do you know if I will be able to run synclient on 18.04.

Thanks
Ralph

---

### Post by vasa1 on 2018-02-16
18.04 will still have Xorg. And Xorg will be the default.

Firefox is now a gtk3 app and the GNOME devs have modernized scrolling. Google Chrome doesn't have this feature.

---

### Post by vasa1 on 2018-02-17
By the way, which theme are you using? Is it the default Greybird theme?

---

### Post by Ralph L on 2018-02-17
I generally run Clearlooks-Phenx, but just to test if the theme made a difference, I went back to greybird, but it didn't change the very rapid repeat of "page at a time" scrolling to the bottom/ top of the web page.

---

### Post by vasa1 on 2018-02-17
> **Ralph L said:**
> I generally run Clearlooks-Phenx, but just to test if the theme made a difference, I went back to greybird, but it didn't change the very rapid repeat of "page at a time" scrolling to the bottom/ top of the web page.

Well, there maybe good news when Xubuntu 18.04 comes around. I looked very briefly at scrolling in Firefox in a Xubuntu 18.04 VM Clicking in the scrollbar area scrolls the page up or down to the area where the cursor is, and no further, even if one keeps pressing the mouse key.

---

### Post by Impavidus on 2018-02-17
In the meantime (as 18.04 is still 2 months away), there's Xubuntu 17.10. I found the upgrade from Xubuntu 17.04 to 17.10 the smoothest ever. And it's still Xorg. The upgrade may be slightly less smooth now that 17.04 is dead. I always try the live disk before upgrading.

---

### Post by Ralph L on 2018-06-15
Does anybody know if any progress has been made in resolving the problem of clicking on the vertical slide and having the slide rapidly and erroneously race to the bottom/top of the page.  As I understand it when I click on the slide trough, the slide should move to my pointer position and stop.  Instead it very rapidly runs right past my pointer position to the bottom or top of page.  Very annoying!!!!!

There was some indication that this might be fixed in xubuntu 18.04, but "no cigar".  I tried the fixes in [https://askubuntu.com/questions/774200/how-to-fix-the-scrollbar-new-behaviour-in-firefox](https://askubuntu.com/questions/774200/how-to-fix-the-scrollbar-new-behaviour-in-firefox) , but they don't work.  I also downloaded kubuntu 18.04 and tried it on several applications (Dolphin, Firefox, some settings menu).  Randomly, it sometimes worked and sometimes didn't.

Anybody have a fix for this problem, or know of fix?  This is my number 1 annoyance with xubuntu, and judging from my tests on kubuntu, is probably a problem in all of ubuntu.

Any help is really, really appreciated!!!!!!!!!

---

### Post by Impavidus on 2018-06-16
> **Ralph L said:**
> Does anybody know if any progress has been made in resolving the problem of clicking on the vertical slide and having the slide rapidly and erroneously race to the bottom/top of the page.  As I understand it when I click on the slide trough, the slide should move to my pointer position and stop.  Instead it very rapidly runs right past my pointer position to the bottom or top of page.  Very annoying!!!!!

I never scroll this way myself (always use the mouse wheel or the keyboard), but I found your reported behaviour when right-clicking on the scrollbar and your wanted behaviour when left-clicking on the scrollbar. That's on Xubuntu 17.10.

---

### Post by Ralph L on 2018-06-16
Impavidus:  Thank you for responding.  I appreciate it.
On my laptop different apps behave differently, when clicking on the slider trough.  Also, holding the Shift button, when clicking in the trough, sometimes changes behavior. Right clicking on some apps causes the slider to slowly scroll. On other apps it has no effect.  Please note that I have an Elan clickpad (great big, one contact button touchpad), and I have made some changes to its behavior using Synaptics/Synclient configuration files.  Here is the behavior I get:

Firefox:  Left-click, slider pages/races to top/bottom; Right-click, does nothing; Shift-Left-click, slider jumps (rather than pages) to pointer location.
Thunar:  Left-click, slider pages/races to top/bottom; Right-click, does nothing; Shift-Left-click, same as Left-click.
Mousepad:  Left-click, slider pages to top/bottom; Right-click, slider slowly scrolls to top/bottom, Shift-Left-click, slider jumps (rather than pages) to pointer location.
LibreOffice Writer:  Left-click, slider pages to pointer location; Right-click, does nothing; Shift-Left-click, same as Left-click.
Thunderbird:  Left-click, pointer pages/races to top/bottom; Right-click, does nothing; Shift-Left-click, slider jumps (rather than pages) to pointer location.

So I guess my conclusion is that Xubuntu (and probably all the Ubuntu family) have a significant problem in this area--very annoying behavior and no consistency.  Plus I can't find any parameters to change behavior.

Anybody else know of things that can be done to fix this problem??????????

---

### Post by The Cog on 2018-06-16
I have come to the conclusion that the problem is the clearlooks-phenix theme that is at fault. It seems that there is a one-pixel area at the right hand side that phenix-clearlooks doesn't recognise as being part of the slider. You can see the block change colour as you mouse over it, and the colour changes back when you reach the very right-hand pixel.

Another symptom of what I think is an error in calculation of the window size is that if I use a KVM guest with the guest screen set to the same size as the host screen, then full-screen the guest, I get scroll bars appearing. Or if I set KVM to scale the guest when in full screen mode, the screen goes slightly blurred as the guest is being scaled to on pixel smaller than the real screen. This only happens with clearlooks-phenix theme.

I have given up on clearlooks-phenix for these reasons and use clearlooks instead, which is a shame because I prefer the appearance of clearlooks-phenix.

---

### Post by Ralph L on 2018-06-16
The Cog:  Thank you for your response.
I see the change in color change you refer to, when I mouse over the slider.  However, I changed to greybird and to clearlooks, and the color of the slider also changed, when I moused over it.  Also, under greybird and clearlooks the slider behavior I listed for the various apps above did not change.  So I don't think a different theme is going to fix my slider movement problem.

---

### Post by The Cog on 2018-06-16
Ah, sorry. We are talking about different things. When I want to scroll I always grab and drag the slider itself, so I hadn't noticed your problem. I had to re-read your post before I understood. My problem with clearlooks-phenix is that when I try to grab the slider at the very right hand edge it misses the slider and triggers the problem you are complaining about.

Sorry, I have no idea how to change the behaviour you are complaining of.

---

### Post by Ralph L on 2018-06-17
The Cog:  I now understand the problem that you have been describing.  Yes, I have that problem also and it too is annoying.  Maybe I will try to post a comment for the author of Clearlooks-Phenix.

---

### Post by Ralph L on 2018-06-17
The Cog:  I posted a comment on the Clearlooks-Phenix website about the narrow band clicking malfunction.  If you could re-enforce that comment with your own post, it would probably help get attention to the problem.  The Clearlooks-Phenix author has responded to other comments I made in the past.

Again, thank you very much for pointing out the narrow band problem.  If we can get that fixed it would help a lot. Getting fixes for the problem of some apps (most notably Firefox, but also Thunar and others) not stopping the slider when the pointer is encountered will probably be harder.

---

### Post by The Cog on 2018-06-17
Ralph L: I searched for a clearlooks-phenix web site and all I could find was [https://github.com/jpfleury/clearlooks-phenix/issues/41](https://github.com/jpfleury/clearlooks-phenix/issues/41). 
Looking in issues, I see that there is an issue "Add scrollbar steppers again" which may help point in the direction of your issue. 

My issue is also listed: "scrollbar slider 1px right-border isnt clickable".

Both these issues have comments that appear to refer to ~/.config/gtk-3.0/config.css (neither issue actually names this file as to where the supplied code should go). I tried adding the 1px fix code to the top of my css file, but after logging out/in again, it still didn't make any difference.

---

### Post by Ralph L on 2018-06-18
The Cog:  Here is the website where I made my comment [https://www.gnome-look.org/default/hive/show/content/145210](https://www.gnome-look.org/default/hive/show/content/145210) . And you pointed me to a website I had not seen before.  Like you, I tried the code and I couldn't make it work.  In fact I tried it in other locations also as recommended by this website:  [https://forum.xfce.org/viewtopic.php?id=11265](https://forum.xfce.org/viewtopic.php?id=11265) Post 4.  I may fiddle around some more.

---

