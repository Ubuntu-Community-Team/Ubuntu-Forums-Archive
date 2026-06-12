---
title: "HOWTO: FutureLooks - A &quot;next-gen&quot; Desktop Pack."
date: 2008-05-16
forum: General Help
---

### Post by Mazza558 on 2008-05-16
**[SIZE="5"]SCREENSHOTS AT BOTTOM OF POST[/SIZE]**

Over the past few months, the software and themes I used have enabled me to reach an absolutely fantastic looking desktop, using a combination of natural green wallpapers and themes which fit well together. 

I therefore decided to create a pack with all the files required to get your desktop to look like the attached screenshots.

I don't think this combination is original, but simply a combination of several projects which fit very well together. The theme I seem to have created draws ideas from all 3 Desktop OSs. It has the modern and high-quality style of Apple's Mac OSX, the transparency from Vista (toned down), and the quality of Linux themes, as well as an extremely high-quality font which looks crystal clear at small sizes.

I agree that the screenshot I gave will give you visions of Vista (e.g clock in right-hand corner, the menu I'm using). However, if you decide not to install the menu, you could achieve something like the second, blue screenshot. I don't think this second screenshot looks anything like Vista.

[B]
The pack I've created features:[/B]
-A modified emerald theme with transparency seamlessly blending into windows. No Vista or OSX theme looks this good.
-Transparent panel backgrounds of your choice
-A small selection of green nature backgrounds reminiscent of OSX Leopard and some Vista wallpapers (They just look good with this theme)
-The beautiful Rainlendar calender, which has just as much functionality as its looks.
-An extremely moddable panel called "Ubuntu System Panel". You're free to try this out, but it requires a bit more effort to fit your tastes.

**You need:**
-Compiz and Emerald
-Ubuntu Gutsy or Hardy

You can download the pack here:

[http://www.mediafire.com/?txvgz9c1ini]("http://www.mediafire.com/?txvgz9c1ini")

Extract it to your desktop and you'll have the FutureLooks folder ready to access.

Please note that you can modify absolutely any aspect of the theme, as emerald and the menu provide an infinite level of customization. It's easy to make the emerald theme fit with a dark Gtk, for example.



                  **[SIZE="5"]HOWTO[/SIZE]**


**Theme**

- It's just Clearlooks, so apply it from the appearance manager.

**Icons**

- Open the "Icons" folder in the pack and the appearance manager.
- Drag the CrashBit file into the appearance manager window.
- Apply the icon theme

**Fonts**

- Open the "Fonts" folder and your home directory.
- In "home", create a folder called ".fonts".
- Copy the font files into this folder.
- Change your fonts to Liberation Sans, size 8, through the appearance manager.

**Calendar**

- Open the "Calendar" folder and open the Rainlendar deb file. Install it.
- Run it from Applications > Office. 
- To set it to boot at startup, open the sessions manager, click "add", Choose a name (e.g calendar) and for the command, put "rainlendar2".

**Emerald Theme**

- Install emerald if you haven't already, with ```
sudo aptitude install emerald
```
- Open the emerald manager.
- Click "import theme"
- Find the GommoMod file and open it in emerald to apply it.
- If you're on Gutsy with an ATi card, press Alt + F2 to open the run box and type ```
emerald --replace
```.

**Ubuntu System Panel**

- Follow the instructions in the "Menu" folder to install. More help for this is on the google code page, which you can find from the instructions.

**Panel Background**

- Open this folder. Copy the backgrounds to a permanent folder (e.g pictures) and then apply them from the gnome panel preferences.

**Wallpapers**

- Copy the ones you want to use to a permanent folder (e.g pictures), then open one, go to the "image" menu and click "set as wallpaper".

**Screenlets**

- This is for the clock in the screenshots. Run

> sudo aptitude install screenlets

To install. The screenlets manager is found in System > Preferences.

**Conclusion**

Credits are located in the pack. 


Hope people get some fun out of this :)

Screenshot for those not logged in:

[[IMG]http://img399.imageshack.us/img399/79/futurelooks1wx6.th.png[/IMG]](http://img399.imageshack.us/my.php?image=futurelooks1wx6.png)[[IMG]http://img107.imageshack.us/img107/5189/bluexr4.th.png[/IMG]](http://img107.imageshack.us/my.php?image=bluexr4.png)

---

### Post by Mazza558 on 2008-05-16
It's been Dugg: [http://digg.com/linux_unix/Gorgeous_new_Theme_Pack_for_Ubuntu_introduced_FutureLooks]("http://digg.com/linux_unix/Gorgeous_new_Theme_Pack_for_Ubuntu_introduced_FutureLooks")

---

### Post by smartboyathome on 2008-05-16
Nice job! It looks awesome and modern! I like. :D

EDIT: Except for USP, that one I have never liked. :(

---

### Post by Mazza558 on 2008-05-16
> **smartboyathome said:**
> Nice job! It looks awesome and modern! I like. :D

EDIT: Except for USP, that one I have never liked. :(

Well, the pack is a kind of "pick and mix". I could have created an install script, but I thought people would prefer to choose how much or little they take from the pack.

---

### Post by billgoldberg on 2008-05-16
It looks good, not exactly to my taste, but something like this would make a good "default" theme for a distro.

---

### Post by Tundro Walker on 2008-05-16
Should move this to the "How To" section so it's saved for posterity.

---

### Post by soapytheclown on 2008-05-16
how did you alter your file manager to look like that?? or is it not nautlius? it looks much better than the default layout imo!!

---

### Post by smartboyathome on 2008-05-16
> **soapytheclown said:**
> how did you alter your file manager to look like that?? or is it not nautlius? it looks much better than the default layout imo!!

That is Thunar, XFCE's file manager. I don't think it can replace nautilus for the desktop. :(

---

### Post by bigbrovar on 2008-05-16
cant seem to install from subversion everytime i try i get this [PHP]/Download/SVN$ svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
svn: REPORT request failed on '/svn/!svn/vcc/default'
svn: REPORT of '/svn/!svn/vcc/default': 400 Bad Request (http://ubuntu-system-panel.googlecode.com)
[/PHP] what gives !

---

### Post by soapytheclown on 2008-05-16
> **smartboyathome said:**
> That is Thunar, XFCE's file manager. I don't think it can replace nautilus for the desktop. :(


ahh i see, i just installed it to see, gotta admit imo the layout just looks so much cleaner to that of nautilus!

---

### Post by zmjjmz on 2008-05-16
I can't get USP to show up in "add to panel"
I followed the instructions on the Google code site...

---

### Post by bsharp on 2008-05-16
Amazing, I'm installing it now.

---

### Post by Mazza558 on 2008-05-16
> **smartboyathome said:**
> That is Thunar, XFCE's file manager. I don't think it can replace nautilus for the desktop. :(

Glad to see everything worked fine for you, according to that screenshot. :)

> **zmjjmz said:**
> I can't get USP to show up in "add to panel"
I followed the instructions on the Google code site...

Try logging out and back in again.

> **bigbrovar said:**
> cant seem to install from subversion everytime i try i get this [PHP]/Download/SVN$ svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
svn: REPORT request failed on '/svn/!svn/vcc/default'
svn: REPORT of '/svn/!svn/vcc/default': 400 Bad Request (http://ubuntu-system-panel.googlecode.com)
[/PHP] what gives !

That's odd. Does anyone else get this error?

---

### Post by smartboyathome on 2008-05-16
> **bigbrovar said:**
> cant seem to install from subversion everytime i try i get this [PHP]/Download/SVN$ svn checkout http://ubuntu-system-panel.googlecode.com/svn/trunk/ ubuntu-system-panel
svn: REPORT request failed on '/svn/!svn/vcc/default'
svn: REPORT of '/svn/!svn/vcc/default': 400 Bad Request (http://ubuntu-system-panel.googlecode.com)
[/PHP] what gives !

Substitute svn for http, and try again. :)

Also, Everything is working great! The only downside is that gnome-panel uses psuedo transparency, but thats not your fault. :)

---

### Post by Mazza558 on 2008-05-16
> **smartboyathome said:**
> Substitute svn for http, and try again. :)

Also, Everything is working great! The only downside is that gnome-panel uses psuedo transparency, but thats not your fault. :)

Yeah, I hope the gnome devs allow proper transparency in future gnome versions.

---

### Post by forrestcupp on 2008-05-16
It looks a lot like Vista to me.  That's not a bad thing in my opinion.

Edit:
The transparency effect blending into the window is pretty cool.

---

### Post by Mazza558 on 2008-05-16
> **forrestcupp said:**
> It looks a lot like Vista to me.  That's not a bad thing in my opinion.

Edit:
The transparency effect blending into the window is pretty cool.

Without the menu I use, it looks pretty far from Vista IMO.

---

### Post by hessiess on 2008-05-16
ugly :(

---

### Post by FuturePilot on 2008-05-16
USP keeps crashing which causes an Apport message that says "/usr/bin/usp does not apply to any package" to popup every 5 seconds. :shock:

---

### Post by forestpixie on 2008-05-16
> **FuturePilot said:**
> USP keeps crashing which causes an Apport message that says "/usr/bin/usp does not apply to any package" to popup every 5 seconds. :shock:

I was getting that as well, but after rebooting it seems to have gone away.

> 
That's odd. Does anyone else get this error?

It was ok 1 hour ago.

And thanks - I'll see what I think after I've lived with it for a while :)

---

### Post by FuturePilot on 2008-05-16
> **forestpixie said:**
> I was getting that as well, but after rebooting it seems to have gone away.



It was ok 1 hour ago.

And thanks - I'll see what I think after I've lived with it for a while :)

Thanks, I will try rebooting.

---

### Post by Mazza558 on 2008-05-16
> **hessiess said:**
> ugly :(

Each to their own. 

What aspect is ugly?

---

### Post by forestpixie on 2008-05-16
> **FuturePilot said:**
> Thanks, I will try rebooting.

Bum steer - sorry, it still appears to pop it's head up 

:-k

---

### Post by forrestcupp on 2008-05-16
> **Mazza558 said:**
> Without the menu I use, it looks pretty far from Vista IMO.

I think it's mainly the Vista-ish wallpaper, the screenlets on the side that looks similar to Vista's sidebar, and the subtle title bar transparency.

Don't get me wrong, though.  I think you've created a beautiful thing.

---

### Post by Mazza558 on 2008-05-16
> **forestpixie said:**
> Bum steer - sorry, it still appears to pop it's head up 

:-k

Does it actually work correctly? If so, you could uninstall Apport if you wanted.

---

### Post by kk0sse54 on 2008-05-16
Don't like the wallpaper too much but thats always easy to change. other than that pretty cool =D>

---

### Post by forestpixie on 2008-05-16
> **Mazza558 said:**
> Does it actually work correctly? If so, you could uninstall Apport if you wanted.
Well I think it's working correctly - although I'd guess something somewhere isn't quite right.

Though what I do not know, it's a bit hard to tell when all apport say's is the problem doesn't apply to any package.

I won't uninstall it just yet - I'd rather try and get to the bottom of it first... if I can of course :)

---

### Post by Iehova on 2008-05-16
This is really fantastic, very pretty. I'm using it now. B)

Thanks for all your work, and that of all the others involved.

---

### Post by ugm6hr on 2008-05-16
I like :)

My desktop looks like yours now too... except the menu and calendar.

I chose a green GDM theme to match: [http://www.gnome-look.org/content/show.php/Crystal?content=52206](http://www.gnome-look.org/content/show.php/Crystal?content=52206) (with pale green background too)

---

### Post by -gabe-noob- on 2008-05-16
before I download it, can it be made dark? 

I'm kinda into dark stuff. (can provide sample colors if needed)

---

### Post by FuturePilot on 2008-05-16
> **forestpixie said:**
> Bum steer - sorry, it still appears to pop it's head up 

:-k

Darn :(

---

### Post by Mazza558 on 2008-05-16
> **forestpixie said:**
> Well I think it's working correctly - although I'd guess something somewhere isn't quite right.

Though what I do not know, it's a bit hard to tell when all apport say's is the problem doesn't apply to any package.

I won't uninstall it just yet - I'd rather try and get to the bottom of it first... if I can of course :)

I had the same problem when I used USP in Hardy. I just uninstalled Apport and everything was fine. There's no problem with it in Gutsy.

---

### Post by Mazza558 on 2008-05-16
> **-gabe-noob- said:**
> before I download it, can it be made dark? 

I'm kinda into dark stuff. (can provide sample colors if needed)

Yes, but you need to edit the emerald theme, and then find a different GTK of your choice.

---

### Post by -gabe-noob- on 2008-05-16
kk 
that can be done

---

### Post by forestpixie on 2008-05-16
> **Mazza558 said:**
> I had the same problem when I used USP in Hardy. I just uninstalled Apport and everything was fine. There's no problem with it in Gutsy.

Now I think about it, I think this is why I didn't bother with the usp before - didn't think about uninstalling apport tbh - guess I thought it was to do with hardy before it was finally released.

---

### Post by steveneddy on 2008-05-16
Looks like SUSE.

:(

---

### Post by Mazza558 on 2008-05-16
> **steveneddy said:**
> Looks like SUSE.

:(

What does SUSE look like?

---

### Post by smartboyathome on 2008-05-16
> **Mazza558 said:**
> What does SUSE look like?

This:
[1]("http://files.opensuse.org/opensuse/en/5/5b/OS11.0beta1-gnome0.png")
[2]("http://files.opensuse.org/opensuse/en/c/c4/OS11.0beta1-gnome2.png")

---

### Post by forrestcupp on 2008-05-16
> **smartboyathome said:**
> This:
[1]("http://files.opensuse.org/opensuse/en/5/5b/OS11.0beta1-gnome0.png")
[2]("http://files.opensuse.org/opensuse/en/c/c4/OS11.0beta1-gnome2.png")

No way.  It's way better looking than that.

---

### Post by madjr on 2008-05-16
**Mazza558**

how i get **USP** to look like yours, what are your settings?

also, am using linuxmint and it has USP/mintmenu can i make that one look like yours too?

---

### Post by bilal.17 on 2008-05-16
I just installed it and im loving it, its a great theme, except the only thing i didnt like was USP, but overall its a great theme.

---

### Post by Kingsley on 2008-05-17
Wow, USP has come a long way since I last used it 2 years ago. I'm enjoying it on my Fedora 9 install right now.

How did you get the 'shortcuts' menu?

---

### Post by vishzilla on 2008-05-17
Nice work mate! Looks good

---

### Post by tdrusk on 2008-05-17
Show this to Linux Mint.

---

### Post by forestpixie on 2008-05-17
> How did you get the 'shortcuts' menu?

I'd be interested in taht as well

---

### Post by ugm6hr on 2008-05-17
A quick note for ATI users - I seem to have to include the command *emerald --replace* in my Session startup list, or it returns to CLearlooks standard every reboot.

---

### Post by tom-ubuntu on 2008-05-17
Very nice!

Changed it aswell, except for calendar and menu. Looks really nice. Thanky you!

---

### Post by Mazza558 on 2008-05-17
I admit USP does look pretty ugly by default. However, there is so much you can do with it (as you can see from the screenshot in the OP) - which is why it's part of the pack.

To get the shortcuts menu, you need to add the "shortcuts" plugin to USP. You can add it from the settings window, on the first tab.

This is from the PluginInformation on the Google Code page:

> 4. shortcuts Provides a list of quick shortcuts to anything. To add a shortcut, you have to first pin the menu. The pin button is the iconless button in the sidepane. If your sidepane is hidden, minimize any plugin to bring it up. Once you have pinned the menu, drag an icon from anywhere into the shortcuts plugin. The first icon is a little hard to drag, since the area that you have to drag it into is very small. The area is right underneath the plugin title. If you are dragging in the right place, a thin black line will appear. Note: If you drag an icon for a file from Nautilus (not a folder), it probably won't work. Right click on the shortcut, and then select edit. Now edit 'exec' field for the correct program needed to open it. For example, an HTML document will need you to replace the part of the command that says 'nautilus' with 'firefox', and for a pdf file you should replace 'nautilus' with 'evince'.

P.S - anyone else want to show what their desktops look like now they've tried this out?

---

### Post by tom-ubuntu on 2008-05-17
> **ugm6hr said:**
> A quick note for ATI users - I seem to have to include the command *emerald --replace* in my Session startup list, or it returns to CLearlooks standard every reboot.

I installed compizconfig-settings-manager:

```
sudo aptitude install compizconfig-settings-manager
```

start it in System -> Preferences -> Advanced Desktop Effects,
go to category "Effects" -> Window Decoration -> General -> Command

and add the line

```
emerald --replace
```

there. Works aswell.

---

### Post by forestpixie on 2008-05-17
> To get the shortcuts menu, you need to add the "shortcuts" plugin to USP. You can add it from the settings window, on the first tab.

I'm being a bit dense this morning - but I can't see either a settings window or a 1st tab :)

From the scnshot I don't appear to have any tabs - doesn't appear the same as the forums page behind it?

---

### Post by Mazza558 on 2008-05-17
> **forestpixie said:**
> I'm being a bit dense this morning - but I can't see either a settings window or a 1st tab :)

Right click on it in the panel ;)

To add tabs, you need to add a new tab to the Plugin List (e.g "NewTab=(what ever you want)), and then click save.

P.S - Why don't you enable font smoothing in the appearance panel?

---

### Post by forestpixie on 2008-05-17
Well I added a tab and get an error - no modules, I'm afraid that this is all as clear as mud :(

---

### Post by Mazza558 on 2008-05-17
> **forestpixie said:**
> Well I added a tab and get an error - no modules, I'm afraid that this is all as clear as mud :(

Get rid of "plugins" from the list and click "New Tab". Then add "=Applications" to the end of the space in the dialog box, so you get something like

```
newtab=Applications
```

---

### Post by forestpixie on 2008-05-17
I'll have a look later - at my mum's playing with windows

---

### Post by Mazza558 on 2008-05-17
We're getting very close to the front page of Digg, with 61 Diggs as of this post. If we get up to about 100 within 7 hours, it'll be a front page :)

---

### Post by forestpixie on 2008-05-17
> **Mazza558 said:**
> Get rid of "plugins" from the list and click "New Tab". Then add "=Applications" to the end of the space in the dialog box, so you get something like

```
newtab=Applications
```

That didn't work - got a tiny menu with applications.

Edit - got it - nearly :) have now managed to add Shortcuts to the menu - but can't get the old nautilus places in there - any hints and I'll leave you alone.

It's Add - then choose name of plugin - shortcuts in this case.

---

### Post by Mazza558 on 2008-05-17
> **forestpixie said:**
> Tried that - not what I was expecting, don't get the menu at all - this is quite intuitive I'd say ;)

You'll get it eventually. ;)

Now do the same to create another tab. Then you can switch between the 2. Remember to move the tab you want ABOVE the plugins you want in that tab, e.g

newtab
plugin
plugin
newtab
plugin

---

### Post by forestpixie on 2008-05-17
Ok yea - finally can make a pane and call it shortcuts (plugin)

Now to get some shortcuts :)

Edit - well it's really easy - once you've done it :D

Thankyou mazza

---

### Post by KrisScofield on 2008-05-17
Beautiful look for Ubuntu! Much better than the hipster brown default. The only thing I don't like about Ubuntu :lolflag:

---

### Post by Achetar on 2008-05-17
> It is Thunar....but I don't think it can replace nautilus for the desktopNo, it can't. But you can use xfdesktop for that.

NIce theme btw

---

### Post by syko21 on 2008-05-17
> **smartboyathome said:**
> Substitute svn for http, and try again. :)
 
Also, Everything is working great! The only downside is that gnome-panel uses psuedo transparency, but thats not your fault. :)
 
You can set the gnome panel transparency through compiz. Open up ccsm and go to the general options part. Hit the opacity tab all the way at the end and add a rule for gnome-panel.

---

### Post by Nerrep on 2008-05-17
Looks like you made the frountpage :)

Downloading now - looks good!

---

### Post by Mazza558 on 2008-05-17
I'm glad most of you like it, because the Digg crowd certainly don't. Here's a taste of people's opinions:

> 
29 minutes ago
I appreciate the effort toward a new theme, but it's too whimsy and translucent for my liking. I need readable as well as beautiful. (see Fedora)

Meh. I've been using mac4lin lately. Now *thats* gorgeous.

Way to remake Vista.

Sort of summed it up for yourself. Wallpaper, Menu, "Start" Bar, Transparency. It looks just like its Vista reskinned, and you know it.

No I like it also, hell I may even put it on my Linux PC but my point is it just looks like Vista reskinned.


Try and tell me the sidebar looks nothing like Vista... I'm not bashing this but the whole look definately looks inspired by Vista regardless if Linux had some parts first.

I think there are better themes out there, although this one is not bad at all.

I like the general look of the theme. But it's obvious it's supposed to be like Vista. Great looking theme however, congrats it obviously took some work.

Mmmm, a little bit old, not innovative at all.

Too much transparent glass for me. Makes me want to throw stones at it. -_-

even when they add in the compositing and the antialiasing, it still looks like it was designed by committee!

One of the reasons I use ubuntu is because I find Windows dull, this theme goes back to what I'm moving away from. 

Those title bars are ******* illegible

and why does linux always imitate windows, the start menu and task bar are terrible ideas

Its quite good but the title bars are pretty bad and the text for the icons on the desktop is too small and packed together.

Too much transparancy for my taste

hate to burst any linux users bubble, but erm... thats exactly like vista??!?!?!?

It looks exactly like clearlooks, but the title bar is transparent. Also, what's the point of showing off your theme if you're going to take a screenshot of your wallpaper and the default ubuntu icons?? Lame...

gDesklets (or Screenlets) are hideous and poorly designed Vista Gadgets. I love Ubuntu, but for every pretty, well-integrated piece of software, there is 10 more ugly as sin, poorly designed pieces of crap.

Nothing like a window that I can't read the title in.

Reminds me far too much of OS X and Vista all in one; get your own idea, Linux!

vista?

Yuck. It looks as hideous as Vista. why copy a turd... wrong path... wrong path...

Yay! Negativity!

---

### Post by andril on 2008-05-17
Congrats - Thanks for the great theme =D>

---

### Post by KrisScofield on 2008-05-17
Well, that's Digg for you. Every article about Ubuntu gets the same treatment.

---

### Post by Mazza558 on 2008-05-17
Added a special FAQ for digg users. Bah.

---

### Post by kinetek on 2008-05-17
As a Ubuntu-esque user (UbuntuStudio) that found your article from Digg, nice job on the theme.

Looks great. I personally like the glossy, glassy look. Easy on the eyes. Keep up the good work. I will definitely be looking forward to more themes from you in the future.

Installing now...

---

### Post by Mazza558 on 2008-05-17
Apologies for the bitter comments in the Digg article and the FAQ at the top. I'll remove it in a week or so. 

Wish I hadn't submitted it in the first place.

---

### Post by MattBD on 2008-05-17
> **Mazza558 said:**
> Apologies for the bitter comments in the Digg article and the FAQ at the top. I'll remove it in a week or so. 

Wish I hadn't submitted it in the first place.

No, there will be plenty of people who like it, but you know what Digg is like, always loads of trolls going "just get a Mac" or "Ubuntu sucks, FreeBSD is real Unix". It's more important that lots of people see it, after all there were plenty of positive comments.

---

### Post by localzuk on 2008-05-17
As I say over at Digg "Looks good. We need more themes that look this professional. There are too many themes about which look like a 2 year old hit a crayon box."

Congrats

---

### Post by blu3ness on 2008-05-17
playing devil's advocate here:

* Functionality wise, looks a lot like Mint, not necessarily a bad thing
* Lacks polish, gradient tones not consistent on gnome panel and taskbar, shadows
  not controlled, windows lack borders which makes them look awkward and unfinished
* font matters, the screenshots gives me the feeling of not carefully thought-out, 
  random msstcorefonts / bitstream vera sans.
* Dividers in the gradient are too rough, needs more polish. 

An example of a polished theme would be clearlooks, rezlooks, and elegant brit (personal favourite)
[http://www.gnome-look.org/content/show.php/Elegant+Brit?content=74553](http://www.gnome-look.org/content/show.php/Elegant+Brit?content=74553)

Regardless, keep up the good work, most good themes don't just pop out of the gutter (except the vista/mac clones, but we can ignore them for now)

---

### Post by dusk on 2008-05-17
nice vista clone

---

### Post by Mazza558 on 2008-05-17
Here's a non-Vista screenshot for you all, using a different background and the normal gnome layout.

[[IMG]http://img107.imageshack.us/img107/5189/bluexr4.th.png[/IMG]](http://img107.imageshack.us/my.php?image=bluexr4.png)

---

### Post by RetepNamenots on 2008-05-17
I'm trying to apply this on my EeePC, but the theme doesn't seem to be working properly; have I missed something obvious?

This is what I've got so far:

[img]http://i285.photobucket.com/albums/ll75/RetepNamenots/Screenshot.png[/img]

(Sorry about the screenshot window still showing up)

Anyway, as you can see the main window area is a horrible 'Windows' grey, whereas the border seems to be showing up as it should do. Does anyone have any ideas?


**Edit:** Whoops, I didn't select the theme [;)]

Looks great anyway! I was just using the Ubuntu Studio theme previously.

---

### Post by linuksamiko on 2008-05-17
Your theme doesn't look so bad even though it is a bit too much "vista-look-alike". But it is fresh, nice an professional looking.

But maybe you should handle the comments of other people a little better. There are many people out there who might dislike this theme and you can be sure that they will tell you if they don't like it.
And the comment "You can change the wallpaper" or something like this is not the question. Everybody knows that everything is changeable but you posted THIS theme and that is the theme in question.

If you change your theme here and there it will look like the screenshot down there (I hope people understand the irony ;-) )

[IMG]http://www.taclug.org/albums/album01/linux_desktop_screenshot_05_02_2002.jpg[/IMG]

---

### Post by eurostyle360 on 2008-05-17
nice job sticking it to digg users.. i hate them.  they are the most closed-minded group of people ever

---

### Post by b3n87 on 2008-05-17
> **eurostyle360 said:**
> nice job sticking it to digg users.. i hate them.  they are the most closed-minded group of people ever

where did that come from and why do you say that?

---

### Post by ZodiacfreaK on 2008-05-17
Before we get off topic, everyone is entitled to their own opinion and we should not judge groups and stereotype others. If we are supposed to be a kind community, lets act like one. Does anyone have the blue watery background in the second screenshot? I don't run ubuntu but I would love to use it as my background.

---

### Post by Mazza558 on 2008-05-17
> **ZodiacfreaK said:**
> Before we get off topic, everyone is entitled to their own opinion and we should not judge groups and stereotype others. If we are supposed to be a kind community, lets act like one. Does anyone have the blue watery background in the second screenshot? I don't run ubuntu but I would love to use it as my background.

Wallpaper from here:

[http://dimage.deviantart.com/art/Blue-Dock-39084753]("http://dimage.deviantart.com/art/Blue-Dock-39084753")

Sorry about the negativity. I appreciate constructive criticism (like a select few comments in the digg thread), but I really can't stand it when people criticise without helping to improve it or suggest improvements. That's when I get angry and occasionally lash out.

> **b3n87 said:**
> where did that come from and why do you say that?

He was talking about my bitter replies to some people in the Digg article (there's a link on the second post of this thread).

EDIT: Wow, 18,000 views.

---

### Post by ZodiacfreaK on 2008-05-17
Thanks so much man!

---

### Post by forestpixie on 2008-05-17
> EDIT: Wow, 18,000 views.

That's not 18,0000 negative views either :D - I personally wouldn't know a vista theme from the back end of a friesian.

Keep it up, I fiddled with the usp before as you know but couldn't get it working.

Take it all with a pinch of salt, people are just that - other people.

Have a medal.

---

### Post by mmb1 on 2008-05-17
Nice job, i like it a lot.  I ducked out on the USP, though, mostly just because I'm a pansy.  :)

---

### Post by armitage1337 on 2008-05-17
Any chance of a KDE version?

---

### Post by Fafnr on 2008-05-17
I'm having some trouble getting all of this to work...

I'm following your guide, and I've never change my theme before, so some of these may be stupid questions. :-)

First of all:
You guide says
"Theme

- It's just Clearlooks, so apply it from the appearance manager."
Apply what? The only theme-file is in Emerald Theme and appearance manager doesn't recognize this file.

My other problem is with transparency. The menu-bar of my windows are transparent (the one you can double-click to have the window "roll" up into itself) but nothing else is. How do I replicate your screenshot where your term is transparent?

I have the exact same problem with USP - I've added gnome-panel to compiz config, but USP is ugly as ever. 

Another guide on how to make USP look nice would also be much appreciated. :-)

Also perhaps some note on how to get emerald to apply the theme on every boot, for those of us who are new to this?

Love the theme, though!

Regards,

Søren Andersen

---

### Post by ghindo on 2008-05-17
Congrats on making the front page of Digg!

---

### Post by TomtheWombat on 2008-05-17
0.71 or 71%.  *Not* 0.71%

---

### Post by mmb1 on 2008-05-17
For everyone who wants to replace nautilus with thunar, as seen in the original screenshots, take a look:

[http://tenjinonline.blogspot.com/2007/03/thanks-to-psychocats-site-i-have-dumped.html](http://tenjinonline.blogspot.com/2007/03/thanks-to-psychocats-site-i-have-dumped.html)

---

### Post by Zealousy on 2008-05-17
I gotta hand it to you, it look all right.  Don't get me wrong here, by no means am I a "Mac fanboy".  In fact I'm using a Linux machine right now.  I just wish that someone would design an interface as elegant and intuitive as the OSX interface.  The man who designed that interface is a genius.

---

### Post by Mazza558 on 2008-05-17
> **Fafnr said:**
> I'm having some trouble getting all of this to work...

I'm following your guide, and I've never change my theme before, so some of these may be stupid questions. :-)

First of all:
You guide says
"Theme

- It's just Clearlooks, so apply it from the appearance manager."
Apply what? The only theme-file is in Emerald Theme and appearance manager doesn't recognize this file.

My other problem is with transparency. The menu-bar of my windows are transparent (the one you can double-click to have the window "roll" up into itself) but nothing else is. How do I replicate your screenshot where your term is transparent?

I have the exact same problem with USP - I've added gnome-panel to compiz config, but USP is ugly as ever. 

Another guide on how to make USP look nice would also be much appreciated. :-)

Also perhaps some note on how to get emerald to apply the theme on every boot, for those of us who are new to this?

Love the theme, though!

Regards,

Søren Andersen

Sorry for being unclear about this. The clearlooks theme is available via the appearance manager, and comes with Ubuntu.

---

### Post by ricochet1269 on 2008-05-17
Maybe I am just being a total n00b, but when I try and install USP, I can get to the point:
> ./usp_update install fresh

When I do that, I get:
> bash: ./usp_update: No such file or directory

I followed the directions, what am I doing wrong?

Thanks in advance.

Nevermind, I figured it out.

---

### Post by bishop9226 on 2008-05-17
does the sidebar/calendar/clock and all those nice apps come ready once you follow all the main steps?  or do i need to do something extra?  i miss my google sidebar from windows:(

---

### Post by -gabe-noob- on 2008-05-17
the white has grown on me this is how I have it settup: 

Like the background? I think it fits (it's one I created :P)

---

### Post by Draton on 2008-05-17
The Emerald theme is not properly making my panels/some of my windows transparent on my system (They are opaque).  Anything I can do to fix this?

---

### Post by Mazza558 on 2008-05-17
Well, I have a new version of the emerald theme. I've toned down the transparency so that wherever the windows are on your desktop, the titles remain legible. To compensate, I've created a kind of "blur" around the edges of inactive windows to distinguish them. I'll also update some of the other elements of the pack based on feedback (e.g non-vegetation wallpapers!)

Give it a go, from this link:

[http://www.filedropper.com/gommomod2]("http://www.filedropper.com/gommomod2")

EDIT: One thing I forgot to do was change the font for the titlebars. They were supposed to be liberationSans, size 8.

---

### Post by Emblem Parade on 2008-05-17
I love it, and I'm hard to please!

Comments:

1. Why not include a GNOME theme? ClearLooks is the appropriate widget theme, but you also want to modify colors a bit. I gave mine a nice green tint, to match the dewey backgrounds.

2. Liberation fonts are already in the Ubuntu repositories, package: ttf-liberation. Or perhaps the ones you are including are modified somehow? Wasn't clear to me.

3. Any ideas how to make Firefox (3) look better with this?

---

### Post by Mazza558 on 2008-05-17
> 1. Why not include a GNOME theme? ClearLooks is the appropriate widget theme, but you also want to modify colors a bit. I gave mine a nice green tint, to match the dewey backgrounds.

I might provide some other matching gtk themes in the future (I'm eyeing Aurora at the moment).

> 2. Liberation fonts are already in the Ubuntu repositories, package: ttf-liberation. Or perhaps the ones you are including are modified somehow? Wasn't clear to me.

Thanks for telling me this, as I had no idea. It'll make things a lot easier (esp. if I want to change the emerald font to liberation).

> 3. Any ideas how to make Firefox (3) look better with this?

Can you attach a screenshot? What aspect looks bad?

---

### Post by Emblem Parade on 2008-05-17
Ah, I restarted Firefox and now it looks OK now. The problem is how Mozilla implemented their Gtk-friendliness... it happens only on start (I guess this is the same reason why you need to restart Firefox when changing themes). You might want to include a comment about this in your howto, in case other users are as think as me...

I'll look into Aurora, too!

---

### Post by Mazza558 on 2008-05-17
Here's a mod for all you Murrina fans. I've modded emerald to create GommoGilouche, for use with MurrinaGilouche (available on gnome look)

[http://www.filedropper.com/gommogilouche]("http://www.filedropper.com/gommogilouche")

---

### Post by speedemonV12 on 2008-05-17
this theme is sick.. using it right now.. great work..

---

### Post by vexorian on 2008-05-17
hmnn I miss the times in which title bars were... title bars, now are they just a neat looking rectangle you can use to move windows?

---

### Post by Fepereir on 2008-05-17
Very nice theme, but I'm having trouble getting the transparency on the window borders, I've managed to make the top/bottom panels transparent, but I can't make anything else transparent (can't find Gnome-panel-preferences)...

Thanks for this awesome theme.

---

### Post by dusk on 2008-05-17
this guy totally copied your theme, bro!

[img]http://www.codeguru.com/dbfiles/get_image.php?id=10605&lbl=SIDEBAR_JPG&ds=20050916[/img]

[go get him!](http://en.wikipedia.org/wiki/Bill_Gates)

---

### Post by vexorian on 2008-05-17
1. Billy didn't invent vista's theme, so we can't blame him for that.
2. The theme on the first post and many screenshots for alternatives, actually look much better than that, and there are many difference.s

---

### Post by hotweiss on 2008-05-17
Beautiful themes! Maybe it's time that to add these as a standard option?

---

### Post by razlken on 2008-05-17
great theme, everything worked, it's just that i can't make the window borders transparent, it seems emerald doesn't do anything at all, maybe i'm doing something wrong please answer, Thanks anyway

---

### Post by PsyWolf on 2008-05-17
Do you think you could possibly make a 32 pixel gradient for the top panel (aka panel 1)?

---

### Post by Mazza558 on 2008-05-17
> **razlken said:**
> great theme, everything worked, it's just that i can't make the window borders transparent, it seems emerald doesn't do anything at all, maybe i'm doing something wrong please answer, Thanks anyway

Can you post a screenshot?

---

### Post by PsyWolf on 2008-05-17
> **Fepereir said:**
> Very nice theme, but I'm having trouble getting the transparency on the window borders, I've managed to make the top/bottom panels transparent, but I can't make anything else transparent (can't find Gnome-panel-preferences)...

Thanks for this awesome theme.


> **razlken said:**
> great theme, everything worked, it's just that i can't make the window borders transparent, it seems emerald doesn't do anything at all, maybe i'm doing something wrong please answer, Thanks anyway

do you have compiz installed and enabled?

You can enable compiz in System> Preferences > Appearances, going to the visual effects tab, and choosing anything other than none.  If your video card doesn't support these effects, you can't use emerald.

then you have to tell compiz to use emerald instead of the default window decorator (metacity).  The easiest way to do this in my opinion is to install fusion-icon by either searching for it in the synaptic package manager or installing by typing this into the terminal and pressing enter.
```
sudo apt-get install fusion-icon
```

once it is installed start it by pressing ALT+F2, typing in fusion-icon and pressing enter.  Finally right click on the icon that should have appeared in your system tray, hover over "Select Window Decorator" and choose "Emerald" instead of "GTK window decorator".  Fusion-icon also gives you easy access to compiz and emerald's extra options, so i have it run at startup.  if you have trouble with that, feel free to ask.

---

### Post by razlken on 2008-05-17
yes i have compiz-fusion installed, did everything for the decoration window etc.. and my graphic card is an integrated Graphic Chip don't know exactly which one.

here is the screen shot

---

### Post by Brii on 2008-05-17
What does he mean by open "emerald manager" where do i go to open it

i already installed it

---

### Post by altonbr on 2008-05-17
I'm sorry, but the title bars are way to hard to read and their are too many transparencies. It looks cheap and tacky.

Gradients are much needed to show depth, but town down the transparency around the borders and make your gradients 'richer' or 'sharper' and I think you'll have something.

---

### Post by evaldas on 2008-05-17
what's the name of that monospace font in the terminal screen from the first post?

---

### Post by armitage1337 on 2008-05-17
> **dusk said:**
> this guy totally copied your theme, bro!

[img]http://www.codeguru.com/dbfiles/get_image.php?id=10605&lbl=SIDEBAR_JPG&ds=20050916[/img]

[go get him!](http://en.wikipedia.org/wiki/Bill_Gates)

Yeah, I can't believe he'd steal it. I think we need to go confront his "Micro-soft" and find out wtf they think they're doing.

---

### Post by Mazza558 on 2008-05-17
> **altonbr said:**
> I'm sorry, but the title bars are way to hard to read and their are too many transparencies. It looks cheap and tacky.

Gradients are much needed to show depth, but town down the transparency around the borders and make your gradients 'richer' or 'sharper' and I think you'll have something.

If you look a few posts above, you'll find a version with much less transparency.

> **evaldas said:**
> what's the name of that monospace font in the terminal screen from the first post?

Monospace.

> **razlken said:**
> yes i have compiz-fusion installed, did everything for the decoration window etc.. and my graphic card is an integrated Graphic Chip don't know exactly which one.

here is the screen shot

What does 

> emerald --replace 

show?

---

### Post by melenor on 2008-05-17
Allright i like the look, mostly i think that the icons look kinda poor in my opinion, otherwise it seems to me, from what i have been able to test looks great. The deb files are only 32-bit plans on releasing any 64-bit versions? that would be great so i could try to look all together.

---

### Post by eurostyle360 on 2008-05-17
> **Mazza558 said:**
> Well, I have a new version of the emerald theme. I've toned down the transparency so that wherever the windows are on your desktop, the titles remain legible. To compensate, I've created a kind of "blur" around the edges of inactive windows to distinguish them. I'll also update some of the other elements of the pack based on feedback (e.g non-vegetation wallpapers!)

Give it a go, from this link:

[http://www.filedropper.com/gommomod2]("http://www.filedropper.com/gommomod2")

EDIT: One thing I forgot to do was change the font for the titlebars. They were supposed to be liberationSans, size 8.

hey.. i love your theme!  you did a great job, but when i tried to add the updated .emerald file i get an error saying "Error calling tar." in emerald.  any ideas why this happens?  the original emerald file worked fine

---

### Post by vickers500 on 2008-05-17
Please provide a guide on how to make the USP look like that, I am as noobish as someone can get on ubuntu, but I already have the other parts of your theme working, just tell me what settings I need to type in or what I need to do to make my thunar usp look like that.

---

### Post by altonbr on 2008-05-17
Make sure to post your work at [email]ubuntu-art@lists.ubuntu.com[/email] because, although I still think their is too much transparency for regular Ubuntu users (and seniors), its much better than what most have out their (or are submitting to this list).

Either post this thread, or make a small little website with 2 screenshots, a .tar.gz and instructions on how to install.

What the current movement is, is making a Launchpad project and loading the theme in Bazaar and letting people hack at it.

You might want to consider one of these so your theme gets more visibility with developers.

---

### Post by Fepereir on 2008-05-17
> **PsyWolf said:**
> do you have compiz installed and enabled?

You can enable compiz in System> Preferences > Appearances, going to the visual effects tab, and choosing anything other than none.  If your video card doesn't support these effects, you can't use emerald.

then you have to tell compiz to use emerald instead of the default window decorator (metacity).  The easiest way to do this in my opinion is to install fusion-icon by either searching for it in the synaptic package manager or installing by typing this into the terminal and pressing enter.
```
sudo apt-get install fusion-icon
```

once it is installed start it by pressing ALT+F2, typing in fusion-icon and pressing enter.  Finally right click on the icon that should have appeared in your system tray, hover over "Select Window Decorator" and choose "Emerald" instead of "GTK window decorator".  Fusion-icon also gives you easy access to compiz and emerald's extra options, so i have it run at startup.  if you have trouble with that, feel free to ask.

I got it working, I just had to run that code and re-write the "emerald --replace" thing. The GPU is an X800XL, btw.

---

### Post by Grifter81 on 2008-05-17
It's cool but I really would like to be able to remove and move items in the Ubuntu System Panel. Is there anyone who can provide directions on how to do things with it? Specifically, I'd like to add the Places information that is in the Application Panel.

---

### Post by BilliShere on 2008-05-17
now the only thing we need is a next-gen complete icon set. then it would be truly kick@$$. 
(hint hint) hey.. apple! stop stealing our icon packs.. jeez.

lol

---

### Post by lecter255 on 2008-05-18
> **Mazza558 said:**
> If you look a few posts above, you'll find a version with much less transparency.



Monospace.



What does 

 

show?

hey i try typing in emerald --replace and it works, but then if i close the terminal the window borders disappear. also , if i restart my computer the regular window borders appear. how do i solve these problems? thanks.

---

### Post by ugm6hr on 2008-05-18
> **lecter255 said:**
> hey i try typing in emerald --replace and it works, but then if i close the terminal the window borders disappear. also , if i restart my computer the regular window borders appear. how do i solve these problems? thanks.

Try one of these: [http://ubuntuforums.org/showpost.php?p=4978135&postcount=49](http://ubuntuforums.org/showpost.php?p=4978135&postcount=49)

---

### Post by Nav2k4 on 2008-05-18
First of all this is an awsome theme pack, great work!. I was wanting to know how to get the shortcuts plugin on the right hand side of applications...

---

### Post by forestpixie on 2008-05-18
Add a newpane with New Pane

Then add shortcuts plugin with the Add button, enter shortcuts as plugin name, you can see that I have shortcuts and places on the same pane.

---

### Post by belovedmonster on 2008-05-18
Just judging by the first screenshots posted, the active window needs to be more clearly visible as the active window. At the mo its almost impossible to tell at a glance that is the active window. This is **BAD**! Eye candy should not make using the computer harder!

Edit: A lot of the highest voted replies on Digg agree with me.

---

### Post by Nav2k4 on 2008-05-18
awsome thanx forestpixie, thar worked.

---

### Post by Mazza558 on 2008-05-18
> **belovedmonster said:**
> Just judging by the first screenshots posted, the active window needs to be more clearly visible as the active window. At the mo its almost impossible to tell at a glance that is the active window. This is **BAD**! Eye candy should not make using the computer harder!

Edit: A lot of the highest voted replies on Digg agree with me.

Again, I've posted a much-improved theme further back in the thread. It fixes a lot of problems people were complaining about.

> **altonbr said:**
> Make sure to post your work at [email]ubuntu-art@lists.ubuntu.com[/email] because, although I still think their is too much transparency for regular Ubuntu users (and seniors), its much better than what most have out their (or are submitting to this list).

Either post this thread, or make a small little website with 2 screenshots, a .tar.gz and instructions on how to install.

What the current movement is, is making a Launchpad project and loading the theme in Bazaar and letting people hack at it.

You might want to consider one of these so your theme gets more visibility with developers.

I'll consider this when I have a little more time ... exams are on my doorstep.

> **eurostyle360 said:**
> hey.. i love your theme!  you did a great job, but when i tried to add the updated .emerald file i get an error saying "Error calling tar." in emerald.  any ideas why this happens?  the original emerald file worked fine

Can anyone else see if they have the same problem?

> **vickers500 said:**
> Please provide a guide on how to make the USP look like that, I am as noobish as someone can get on ubuntu, but I already have the other parts of your theme working, just tell me what settings I need to type in or what I need to do to make my thunar usp look like that.

If I have the time. For now, you can check out the wiki on USP's Google Code page - this provides plenty of info.

> **melenor said:**
> Allright i like the look, mostly i think that the icons look kinda poor in my opinion, otherwise it seems to me, from what i have been able to test looks great. The deb files are only 32-bit plans on releasing any 64-bit versions? that would be great so i could try to look all together.

It depends whether the Rainlendar devs want to make a 64-bit deb file. What else doesn't work on 64-bit?

---

### Post by forestpixie on 2008-05-18
I just downloaded both of you're new emerald themes - got error calling tar for both.

---

### Post by Mazza558 on 2008-05-18
> **forestpixie said:**
> I just downloaded both of you're new emerald themes - got error calling tar for both.

That's odd. I'll look into it later.

---

### Post by forestpixie on 2008-05-18
That's cool - just letting you know.

---

### Post by K.Mandla on 2008-05-18
Moved to Desktop Effects and Customization.

---

### Post by razlken on 2008-05-18
using ```
emerald --replace
``` worked perfectly, but when i close the terminal, the border simply disappears from all windows...that's not normal right? any solution?

---

### Post by Mazza558 on 2008-05-18
> **razlken said:**
> using ```
emerald --replace
``` worked perfectly, but when i close the terminal, the border simply disappears from all windows...that's not normal right? any solution?

Add it to the sessions manager - then it'll always be enabled.

---

### Post by ASULutzy on 2008-05-18
Sorry if this was answered previously, but 15 pages is a lot of stuff to dig through.

Where did you get the wallpaper you used in the screenshots you've attached? I downloaded that pack and it has a lot of the "grass" ones, but I can't seem to find that "ocean and clouds" one

---

### Post by SlalomMan on 2008-05-18
I'm looking to switch completely over from ubuntu's default brown theme; has anyone found a login screen that goes good with this? When I boot up it goes from that bland brown login screen to the transparent blue/green desktop I have now, and I don't really like it.

---

### Post by forestpixie on 2008-05-18
> **ASULutzy said:**
> Sorry if this was answered previously, but 15 pages is a lot of stuff to dig through.

Where did you get the wallpaper you used in the screenshots you've attached? I downloaded that pack and it has a lot of the "grass" ones, but I can't seem to find that "ocean and clouds" one
[http://dimage.deviantart.com/art/Blue-Dock-39084753](http://dimage.deviantart.com/art/Blue-Dock-39084753)

---

### Post by razlken on 2008-05-18
Thanks it worked great!

---

### Post by FLCLFan on 2008-05-18
That USP is 100% vista!

Err.

---

### Post by fwre01 on 2008-05-18
Mazza558 i like the screenshot on the right at the bottom of your post, could you tell me where you got the desktop background??

....or does anyone else know where to get the blue ocean background??

---

### Post by HoldSteady on 2008-05-18
I'm sure TLLTS guys would love the 'big-***' clock. ;)

---

### Post by Mazza558 on 2008-05-18
> **fwre01 said:**
> Mazza558 i like the screenshot on the right at the bottom of your post, could you tell me where you got the desktop background??

....or does anyone else know where to get the blue ocean background??

Look a few posts above you ;)

---

### Post by Tu13erhead on 2008-05-18
> **forestpixie said:**
> I just downloaded both of you're new emerald themes - got error calling tar for both.

Same here.

---

### Post by Mazza558 on 2008-05-18
Hopefully this new version of the emerald theme fixes things... (e.g actually works)

[http://www.filedropper.com/gommomod21]("http://www.filedropper.com/gommomod21")

Please test ASAP. Thanks :)

---

### Post by forestpixie on 2008-05-18
Error calling tar I'm afraid.

---

### Post by Mazza558 on 2008-05-18
> **forestpixie said:**
> Error calling tar I'm afraid.

Still?

It works fine here... then again, I'm on Gutsy. I wonder why the first one added fine?

In the meantime, here's the start of the google code page:

[IMG]http://img137.imageshack.us/img137/2057/futurelookswh8.jpg[/IMG]

[http://code.google.com/p/futurelooks/]("http://code.google.com/p/futurelooks/")

---

### Post by fwre01 on 2008-05-18
...i knew that ;)

---

### Post by samurailink3 on 2008-05-18
Great theme!!! Using it now!!

---

### Post by Arlanthir on 2008-05-18
+1 for the Error calling tar on any emerald other than the first posted.
Great concept for the theme, anyway ;)

I think I'll play around with it :D

---

### Post by Stvnx7 on 2008-05-18
I like it! Thanks. The instructions were invaluable. I wish more themes would do this, since there seems to be a variety of different programs and methods, etc., that people use for customization. (It's all very confusing).

---

### Post by fickenbaisage on 2008-05-18
> **Mazza558 said:**
> Hopefully this new version of the emerald theme fixes things... (e.g actually works)

[http://www.filedropper.com/gommomod21]("http://www.filedropper.com/gommomod21")

Please test ASAP. Thanks :)

Still doesn't work for me. I'm using Hardy.

Here's a suggestion: Add an icon theme to your package. This website is great for icons [http://www.iconspedia.com/](http://www.iconspedia.com/)

---

### Post by SlalomMan on 2008-05-18
There is an icon theme with the package...it's in the first post of this thread. It's the CrashBit icon theme.

---

### Post by zhuqing123 on 2008-05-18
The fourth [wow power leveling](http://www.wow-powerleveling.org) latest game in [wow power leveling](http://www.xowow.com) Warcraft series is ‘[wow power leveling](http://www.powerlevelingweb.com)’. Also known as [wow power leveling](http://www.igsstar.com), it represents a [wow power leveling](http://www.wowgoldweb.com) multiplayer online [wow power leveling](http://www.powerleveling-wow.com/siteMap.asp) game, the best of [wow power leveling](http://www.powerleveling-wow.com) kind. Initially, it was [wow gold](http://www.wow-powerleveling.org) it be released in 2001, but [wow powerleveling](http://www.powerleveling-wow.com) was delayed [wow powerleveling](http://www.powerlevelingweb.com) 2004, thus [wow powerleveling](http://www.xowow.com) the 10 years of[wow powerleveling](http://www.wow-powerleveling.org) franchise of this[wow gold](http://www.xowow.com) series. The [world of warcraft power leveling](http://www.powerlevelingweb.com) was not [world of warcraft power leveling](http://www.wow-powerleveling.org/wow+power+leveling.html)fulfilling, because [wow power level](http://www.powerleveling-wow.com/siteMap.asp)problems with [wow power level](http://www.powerlevelingweb.com) server’s stability [power leveling wow](http://www.powerleveling-wow.com/siteMap.asp) performance occurred, but [power leveling wow](http://www.xowow.com) game still [power leveling wow](http://www.powerlevelingweb.com) a financial success [powerleveling wow](http://www.powerleveling-wow.com/siteMap.asp) the most [powerleveling wow](http://www.xowow.com) game of its kind. The number [cheap wow power leveling ](http://www.powerlevelingweb.com) users that play [Maple Story mesos](http://www.igsstar.com/Maple-Story-mesos-us/), exceeds 8.5 [MapleStory mesos](http://www.igsstar.com/Maple-Story-mesos-us/), worldwide.As a form [ms mesos](http://www.igsstar.com/Maple-Story-mesos-us/),recognition for [mesos](http://www.igsstar.com/Maple-Story-mesos-us/),outstanding popularity, the game [SilkRoad Gold](http://www.igsstar.com/Silkroad-Online-Gold/), received a[SRO Gold](http://www.igsstar.com/Silkroad-Online-Gold/), of awards. Now the question [eq2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), why is [eq2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), game [eq2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), popular? For anyone[EverQuest 2 Platinum](http://www.igsstar.com/EverQuest-2-gold-plat/), played the previous [EverQuest 2 gold](http://www.igsstar.com/EverQuest-2-gold-plat/), and [EverQuest 2 plat](http://www.igsstar.com/EverQuest-2-gold-plat/), already initiated [lotro gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the mysterious world [lotr gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), the breathtaking [Lord of the Rings online Gold](http://www.igsstar.com/Lord-of-The-Ring-online-gold/), this [Rolex Replica](http://www.watchreplicashop.com/) nothing but an [Replica Rolex](http://www.watchreplicashop.com/) adventure that continues the story of ‘Warcraft III: Frozen Throne’, four years after conclusion, in the world of Azeroth. The game is online role-playing, the previous versions being online and offline strategy games. The major thrills and unique features are present as in every Blizzard game.

---

### Post by PauGNU on 2008-05-19
Hi, nice theme!!

How can I add the shut down button to the ubuntu system panel?. I was able to add other buttons manually, but didn't find the way to add that button. 

[IMG]http://www.drupload.com/uploads/641usp.png[/IMG]

---

### Post by WorldTripping on 2008-05-19
Gotta say that I'm liking this.

It was the reason that I installed emerald for the first time, and started fiddling.

I'm using the emerald theme, icons, fonts, and transparancies.

Thanks for the pack !

---

### Post by forestpixie on 2008-05-19
> **PauGNU said:**
> Hi, nice theme!!

How can I add the shut down button to the ubuntu system panel?. I was able to add other buttons manually, but didn't find the way to add that button. 

[IMG]http://www.drupload.com/uploads/641usp.png[/IMG]

Is it not in the System Management pane

---

### Post by akxiii on 2008-05-19
> **lecter255 said:**
> hey i try typing in emerald --replace and it works, but then if i close the terminal the window borders disappear. also , if i restart my computer the regular window borders appear. how do i solve these problems? thanks.

what worked for me was going system-preferences-advanced desktop-effects-window decoration 
then in the command box type /usr/bin/emerald --replace

then reboot, it worked perfectly for me :)

*I'm using Hardy and neither of the emerald packs (version2) worked for me.
can you pm me if you post another? I'd love to see it. Got everything running well, but the "start" menu was just taking too much time to fiddle with.

---

### Post by KrisScofield on 2008-05-19
When I run:
emerald --replace

The theme goes back to the default blue clearloooks. How do I keep the emerald theme when I start up?

---

### Post by OmniCloud on 2008-05-19
Can't say that I'm really feeling this man...I see how much work you put into it though, and it's impressive, but its too similar to what's popular out there, and therefore I think your originality gets overlooked. 

For example, here's a few screenshots of my Desktop with fedora. Obviously, I didn't work on it as hard as you, and for linux users, it's fairly standard. However, I got some nice comments and kudos for those shots. Why, because it was just different from Windows or Mac, and a look that only a Linux machine could produce. 

Let's stop feeling like polished means "its similar to this or that" and really just do your own thing. 

Now after all that, I still think your desktop is pretty attractive...:popcorn:

---

### Post by Mazza558 on 2008-05-19
> **OmniCloud said:**
> Can't say that I'm really feeling this man...I see how much work you put into it though, and it's impressive, but its too similar to what's popular out there, and therefore I think your originality gets overlooked. 

For example, here's a few screenshots of my Desktop with fedora. Obviously, I didn't work on it as hard as you, and for linux users, it's fairly standard. However, I got some nice comments and kudos for those shots. Why, because it was just different from Windows or Mac, and a look that only a Linux machine could produce. 

Let's stop feeling like polished means "its similar to this or that" and really just do your own thing. 

Now after all that, I still think your desktop is pretty attractive...:popcorn:

I'm trying to create an easy to use and attractive theme back for Ubuntu - that's all. My first release is hardly original, I'll give you that. Futurelooks 2 and 3 will have a lot more variety, and I hope to work with others to get them released over the next month or so.

---

### Post by Mazza558 on 2008-05-19
Does this emerald theme work?

[http://www.mediafire.com/?tj926tyeeby]("http://www.mediafire.com/?tj926tyeeby")

This time, I've eliminated 2 possible causes of it not working:

- bad upload
- not saving theme before exporting it.

---

### Post by forestpixie on 2008-05-19
Thanks mazza - that works just fine here.

---

### Post by Mazza558 on 2008-05-19
> **forestpixie said:**
> Thanks mazza - that works just fine here.

Yay! Now I can make some real progress.

Any comments about the new version?

I'm considering ways to make active/inactive windows different by using color.

---

### Post by Mazza558 on 2008-05-19
Okay, 2 new mods, for different tastes. I need to update the previews for each one, so it's easier to choose between them. Feel free to delete any you don't like.

Blue Mod (Fits with the Clearlooks theme)

[http://www.mediafire.com/?nmyw8xlcmtm]("http://www.mediafire.com/?nmyw8xlcmtm")

Silver Mod (For a metallic look)

[http://www.mediafire.com/?yi2ymc3le21]("http://www.mediafire.com/?yi2ymc3le21")

---

### Post by forestpixie on 2008-05-19
All 3 downloaded fine - I personally prefer the new blue one - matches the desktop. Bet you'd like a £ for every view now :D

More than happy now I've got the panel working as well.

---

### Post by Draton on 2008-05-19
Everything is looking good except that I still do not have transparency on my panels.  I am attaching a screenshot as an example:
[ATTACH]70735[/ATTACH]

---

### Post by Mazza558 on 2008-05-19
GommoGilouche, for those who prefer Murrina Gilouche.

[http://www.mediafire.com/?iuzg1uzdzxo]("http://www.mediafire.com/?iuzg1uzdzxo")

---

### Post by Mazza558 on 2008-05-19
> **Draton said:**
> Everything is looking good except that I still do not have transparency on my panels.  I am attaching an image as an example:
[ATTACH]70735[/ATTACH]

You need the panel backgrounds found in the pack. Right-click on the panel and click "properties" to choose them.

---

### Post by Garofoli on 2008-05-19
This is a really sweet theme, the only problem that I need to type "emerald --replace" every time I want to view this theme. Anyone know what's wrong? Thanks. :D

---

### Post by Mazza558 on 2008-05-19
> **Garofoli said:**
> This is a really sweet theme, the only problem that I need to type "emerald --replace" every time I want to view this theme. Anyone know what's wrong? Thanks. :D

Add the command to the sessions manager.

---

### Post by Draton on 2008-05-19
Thanks Mazza, worked like a charm!

---

### Post by klato on 2008-05-19
Cool stuff! I'm using the new blue emerald theme.

Also just installed Thunar...man this thing is way faster than Nautilus and nicer looking too.

Thanks!

---

### Post by Mazza558 on 2008-05-19
I don't know if anyone has noticed, but I've removed the border for inactive windows. Looks good?

---

### Post by Calle on 2008-05-19
This package is awesome; however, I can't get the simplest part of them all to work: installing the Clearlooks theme. It keeps saying *There was an error installing the selected file -  "FutureLooks1.0" does not appear to be a valid theme.*
Any ideas on what might be the problem? Any help is appreciated.

---

### Post by thedanf on 2008-05-19
Awesome theme!! Especially liking the emerald theme.. very elegant.

I took bits of your combination, and put it together with some elements of my own.

I don't know how everyone is complaining about the vista-esque look, when it's soooo easy to customize, like I'm about to show you.

P.S. I'm a digg user. We don't all hate you ;)

[IMG]http://img503.imageshack.us/img503/7080/screenshotcu4.th.png[/IMG]

---

### Post by mmb1 on 2008-05-19
> **Calle said:**
> This package is awesome; however, I can't get the simplest part of them all to work: installing the Clearlooks theme. It keeps saying *There was an error installing the selected file -  "FutureLooks1.0" does not appear to be a valid theme.*
Any ideas on what might be the problem? Any help is appreciated.

Clearlooks comes by default with a vanillan Gnome Ubuntu installation.  It should be available by going to system-preferences-apperance-themes. 

Hope this helps.  :)

---

### Post by Mazza558 on 2008-05-19
> **thedanf said:**
> Awesome theme!! Especially liking the emerald theme.. very elegant.

I took bits of your combination, and put it together with some elements of my own.

I don't know how everyone is complaining about the vista-esque look, when it's soooo easy to customize, like I'm about to show you.

P.S. I'm a digg user. We don't all hate you ;)

[IMG]http://img503.imageshack.us/img503/7080/screenshotcu4.th.png[/IMG]

Thanks, glad you liked it :)

Remember that this is only the first release...

---

### Post by altonbr on 2008-05-19
> **Calle said:**
> This package is awesome; however, I can't get the simplest part of them all to work: installing the Clearlooks theme. It keeps saying *There was an error installing the selected file -  "FutureLooks1.0" does not appear to be a valid theme.*
Any ideas on what might be the problem? Any help is appreciated.

I don't thin he has setup the .tar.gz to be able to straight upload into System > Preferences > Appearance. I think its a collection of wallpapers and such instead.

---

### Post by ringer on 2008-05-19
> **razlken said:**
> yes i have compiz-fusion installed, did everything for the decoration window etc.. and my graphic card is an integrated Graphic Chip don't know exactly which one.

here is the screen shot


remember in compiz manager find Window Decoration, and in the Command line type **emerald --replace**

---

### Post by SlalomMan on 2008-05-19
> **Calle said:**
> This package is awesome; however, I can't get the simplest part of them all to work: installing the Clearlooks theme. It keeps saying *There was an error installing the selected file -  "FutureLooks1.0" does not appear to be a valid theme.*
Any ideas on what might be the problem? Any help is appreciated.

Clearlooks is a default theme; its more of a button theme, whereas the emerald theme is the edges and window decoration. Clearlooks should be in your appearance manager.

---

### Post by CAE2685 on 2008-05-19
Is there a way to edit the spelling of "Favourites" for those of us on the other side of the Atlantic?

---

### Post by techstop on 2008-05-19
Nice work! Disappointed to see that Rainlendar is not available for 64-bit though...

---

### Post by Mazza558 on 2008-05-20
> **CAE2685 said:**
> Is there a way to edit the spelling of "Favourites" for those of us on the other side of the Atlantic?

Where's this in the theme? Rainlendar?

---

### Post by PRGUY85 on 2008-05-20
Hey there, for those of you that are using Thunar as your file managers...is there a way to disable Nautilus completely or is it necessary for other processes other than file management.  I don't want to spend resources on Nautilus if I am not using it but you guys let me know.

Other than that, great simple theme.  Here is my current desktop:

[[IMG]http://img166.imageshack.us/img166/5002/screenshotuc5.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshotuc5.png)

---

### Post by OmniCloud on 2008-05-20
> **Mazza558 said:**
> I'm trying to create an easy to use and attractive theme back for Ubuntu - that's all. My first release is hardly original, I'll give you that. Futurelooks 2 and 3 will have a lot more variety, and I hope to work with others to get them released over the next month or so.I got you..on that note, Job well done;)

---

### Post by rocknrolf77 on 2008-05-20
> **PRGUY85 said:**
> Hey there, for those of you that are using Thunar as your file managers...is there a way to disable Nautilus completely or is it necessary for other processes other than file management.  I don't want to spend resources on Nautilus if I am not using it but you guys let me know.

Other than that, great simple theme.  Here is my current desktop:

[[IMG]http://img166.imageshack.us/img166/5002/screenshotuc5.th.png[/IMG]](http://img166.imageshack.us/my.php?image=screenshotuc5.png)

You can replace nautilus : [http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease)

By the way. Super theme. Made me inspired again :)

---

### Post by PRGUY85 on 2008-05-20
I did do this, though Nautilus is still running:

[[IMG]http://img386.imageshack.us/img386/176/screenshotky7.th.png[/IMG]](http://img386.imageshack.us/my.php?image=screenshotky7.png)

You can see Nautilus is still up there and Thunar is open when I open any file management window.  Does the Gnome desktop uses Nautilus for other stuff other than file management?

---

### Post by PRGUY85 on 2008-05-20
Also, anyone know of a good GDM theme to go with this theme.  I mean, I love the original Ubuntu GDM but the orange is out of place now with the theme.

---

### Post by rocknrolf77 on 2008-05-20
Nautilus also draws the background, icons and stuff too. So you can't get totally rid of it using gnome. By the way have you checked out the pcman filemanager? Extra lightweight and supports tabs.

---

### Post by carella on 2008-05-20
Nice work thanks !
But I made a mistake and typed emerald --replace but I am not in Gutsy (Hardy) and I have an nVidia !!!
What to do ?
Because now if I don't run emerald --replace in a terminal I have no borders for my windows
Thanks for your help

---

### Post by Mazza558 on 2008-05-20
> **carella said:**
> Nice work thanks !
But I made a mistake and typed emerald --replace but I am not in Gutsy (Hardy) and I have an nVidia !!!
What to do ?
Because now if I don't run emerald --replace in a terminal I have no borders for my windows
Thanks for your help

Add "emerald --replace" to your sessions manager.

---

### Post by tigersrock on 2008-05-20
Awesome pack! keep on it mazza.

Here's my desktop with the original theme, some of the others didn't work for me in hardy, I'll try the newest ones later.

I found this on digg, don't mind the comments and thanks for sharing. :)

---

### Post by _alex_ on 2008-05-20
Great theme! I'm using it as well :)
Would be nice if it were possible to theme the look of the window list (e.g. active window in the list would look better if it had same gradient & transparency as the panel, except perhaps a blue shade)...

Don't let the digg comments get to you. People always resist change, even if it's for the better; also you can never make something that fits all tastes.

I personally think it's a great theme. I tinkered around with it a little to fit my preferences, but definitely great work, and I hope to see it as a a built-in option in future ubuntu releases.

Alex

---

### Post by Mazza558 on 2008-05-20
> **_alex_ said:**
> Great theme! I'm using it as well :)
Would be nice if it were possible to theme the look of the window list (e.g. active window in the list would look better if it had same gradient & transparency as the panel, except perhaps a blue shade)...

Don't let the digg comments get to you. People always resist change, even if it's for the better; also you can never make something that fits all tastes.

I personally think it's a great theme. I tinkered around with it a little to fit my preferences, but definitely great work, and I hope to see it as a a built-in option in future ubuntu releases.

Alex

I think the window list button controls are managed by the clearlooks engine itself.

---

### Post by _alex_ on 2008-05-20
> **Mazza558 said:**
> I think the window list button controls are managed by the clearlooks engine itself.

Yeah that's what I figured. It seems it uses the button widget, which means it can't be changed without affecting the look of buttons in other applications. I'd love to see something like the attached image though :)

P.S.: I really like the new silver theme :)

---

### Post by rocknrolf77 on 2008-05-20
> **carella said:**
> Nice work thanks !
But I made a mistake and typed emerald --replace but I am not in Gutsy (Hardy) and I have an nVidia !!!
What to do ?
Because now if I don't run emerald --replace in a terminal I have no borders for my windows
Thanks for your help

Install fusion icon. Then you can pick window decorator, restart window manager etc.

Then put fusion-icon in sessions and compiz and emerald will autostart.

---

### Post by akxiii on 2008-05-20
> **KrisScofield said:**
> When I run:
emerald --replace

The theme goes back to the default blue clearloooks. How do I keep the emerald theme when I start up?

dude, i responded on how to do this directly above your post...

---

### Post by CAE2685 on 2008-05-21
> **Mazza558 said:**
> Where's this in the theme? Rainlendar?

Whoops... should have been more specific. Also, I just realized it's part of USP so I'll just head over to their thread and bug them.

---

### Post by Mazza558 on 2008-05-21
> **CAE2685 said:**
> Whoops... should have been more specific. Also, I just realized it's part of USP so I'll just head over to their thread and bug them.

Ah, I see. Remember that here in the UK, "favourites" is the correct spelling" ;)

---

### Post by Mazza558 on 2008-05-21
A sign of things to come ;)

---

### Post by smartboyathome on 2008-05-21
> **Mazza558 said:**
> A sign of things to come ;)

I'm sorry, but I don't like that as much. There is too much blending, while with Human-Clearlooks and my mod there is more contrast. If I were you, I would stick to the current, and just change colors and other things if you want.

---

### Post by Mazza558 on 2008-05-21
> **smartboyathome said:**
> I'm sorry, but I don't like that as much. There is too much blending, while with Human-Clearlooks and my mod there is more contrast. If I were you, I would stick to the current, and just change colors and other things if you want.

It'll be an option in FutureLooks2 - my focus is choice for this release. I'll even cater for those who want to use the Blur plugin in compiz by making a more transparent version. Of course, the option to simply use the normal theme will be there (Clearlooks + GommoMod2)

---

### Post by tigersrock on 2008-05-21
The silver one is definitely the one for me, looks awesome with a bit more darker wallpapers. Btw i like the transparency u are adding.

---

### Post by PsyWolf on 2008-05-22
1) I just wanted to say, that I found a glass theme for Rainlendar2 that i think fits rather nicely (see the screen shot).  [_ Just click here_]("http://customize.org/rainlendar/skins/57259") and download the .zip file, unzip it, and copy it the folder to your rainlendar2 skins folder.  (mine was /usr/share/rainlendar2/skins)  Then restart rainlendar2, go to options and apply the new skin.


2) On a side note, it still bugs me that the gradient on my 32 pixel top panel is upside down because you only made a 32 pixel version of the bottom panel.  I wish i knew enough about the gimp to fix this myself, but i don't.  Could someone please make a 32 pixel version of panel 1.  It seems like it wouldn't be too difficult if you knew what you were doing.

Nice theme!  keep up the good work.

---

### Post by Mazza558 on 2008-05-22
> **PsyWolf said:**
> 1) I just wanted to say, that I found a glass theme for Rainlendar2 that i think fits rather nicely (see the screen shot).  [_ Just click here_]("http://customize.org/rainlendar/skins/57259") and download the .zip file, unzip it, and copy it the folder to your rainlendar2 skins folder.  (mine was /usr/share/rainlendar2/skins)  Then restart rainlendar2, go to options and apply the new skin.


2) On a side note, it still bugs me that the gradient on my 32 pixel top panel is upside down because you only made a 32 pixel version of the bottom panel.  I wish i knew enough about the gimp to fix this myself, but i don't.  Could someone please make a 32 pixel version of panel 1.  It seems like it wouldn't be too difficult if you knew what you were doing.

Nice theme!  keep up the good work.

I love that skin. I might include it in FutureLooks V2.

I'll also create a reverse panel background.

---

### Post by smartboyathome on 2008-05-22
Would you like me to send you my version of your theme? (ubuntu brown) :)

---

### Post by Mazza558 on 2008-05-22
> **smartboyathome said:**
> Would you like me to send you my version of your theme? (ubuntu brown) :)

Yes please, I'll have more time to work on FutureLooks theme tomorrow (after my last exam :))

---

### Post by smartboyathome on 2008-05-22
Here you go. :)

Rename it to .emerald and it will work with emerald theme manager.

---

### Post by Mazza558 on 2008-05-23
I've made a lot of progress. Here's a preview of all the variations so far - I suspect version 2 will be out (beta version) in a few days. Smartboy, I've taken your theme (I like it), and lowered the transparency a bit. It was slightly too hard to read on some backgrounds.

I'm most pleased with FutureMidnight, which I'm finished with. It's the theme farthest to the right and uses AuroraMidnight for the controls. I'm considering adding more dark themes later.

---

### Post by altonbr on 2008-05-23
> **Mazza558 said:**
> I've made a lot of progress. Here's a preview of all the variations so far - I suspect version 2 will be out (beta version) in a few days. Smartboy, I've taken your theme (I like it), and lowered the transparency a bit. It was slightly too hard to read on some backgrounds.

I'm most pleased with FutureMidnight, which I'm finished with. It's the theme farthest to the right and uses AuroraMidnight for the controls. I'm considering adding more dark themes later.

And for metacity people?

---

### Post by smartboyathome on 2008-05-23
> **altonbr said:**
> And for metacity people?

This is made for transparency, and metacity doesn't do transparency. So it would look sort of awkward when not having transparency. It could be done, though. :KS

---

### Post by tigersrock on 2008-05-23
> **PsyWolf said:**
> 1) I just wanted to say, that I found a glass theme for Rainlendar2 that i think fits rather nicely (see the screen shot).  [_ Just click here_]("http://customize.org/rainlendar/skins/57259") and download the .zip file, unzip it, and copy it the folder to your rainlendar2 skins folder.  (mine was /usr/share/rainlendar2/skins)  Then restart rainlendar2, go to options and apply the new skin.


2) On a side note, it still bugs me that the gradient on my 32 pixel top panel is upside down because you only made a 32 pixel version of the bottom panel.  I wish i knew enough about the gimp to fix this myself, but i don't.  Could someone please make a 32 pixel version of panel 1.  It seems like it wouldn't be too difficult if you knew what you were doing.

Nice theme!  keep up the good work.

That rainlendar skin looks good but the tasks window doesn't seem to work

---

### Post by Mazza558 on 2008-05-24
> **tigersrock said:**
> That rainlendar skin looks good but the tasks window doesn't seem to work

Yes, and the tooltips look awful. I don't think I'll include this in FL2.

Oh, and there seems to be a metacity version of Gommoso floating around on gnome-look, I might add that in for everyone else.

---

### Post by PsyWolf on 2008-05-24
ok, so the tasks window is there, but its just completely invisible until you get some tasks in it.  I don't know why, and I don't think there is a way to change it.  I personally don't use the tasks window anyway though, so it wasn't really a problem for me.

I agree about the tooltips.  I mean, all in all, the skin needs alot of work for it to really be polished, but if you ever get around to making rainlendar skins to go with your themes, it would probably be a good baseline, or at least reference.

---

### Post by Mazza558 on 2008-05-24
> **PsyWolf said:**
> ok, so the tasks window is there, but its just completely invisible until you get some tasks in it.  I don't know why, and I don't think there is a way to change it.  I personally don't use the tasks window anyway though, so it wasn't really a problem for me.

I agree about the tooltips.  I mean, all in all, the skin needs alot of work for it to really be polished, but if you ever get around to making rainlendar skins to go with your themes, it would probably be a good baseline, or at least reference.

Yeah. 

I'm releasing Version 2 in a few minutes, just want to check that everything's there. It's vastly, vastly improved from version 1, with loads of new stuff. :)

EDIT: Uploading now!

EDIT 2: It's out! more information here:  [http://ubuntuforums.org/showthread.php?t=806135]("http://ubuntuforums.org/showthread.php?t=806135")

---

### Post by tckrockz on 2008-05-24
thanks for the howto when i tired this i dint get the transperent pannels at the top :( 
how do i get them?

---

### Post by SkonesMickLoud on 2008-05-24
> **tckrockz said:**
> thanks for the howto when i tired this i dint get the transperent pannels at the top :( 
how do i get them?

Copy the three files contained in the "Panel Backgounds" folder to a permanent folder (i.e. Pictures), then right click on a blank space on the panel, select Properties >> Background, select the radio button for "Background Image", then navigate to and select whichever picture looks the best.

---

### Post by sports fan Matt on 2008-05-24
Im having trouble installing the theme can anyone help? I accidently uninstalled alot of the clearlooks themes so I need help, after extraction, the themes arent there..Can anyone help?

---

### Post by gingin on 2008-05-25
does any body had such note from Terminal?
How to solve this?

gin@linux-laptop:~$ emerald --replace

(emerald:6448):GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

---

### Post by Mazza558 on 2008-05-25
> **sox fan Matt said:**
> Im having trouble installing the theme can anyone help? I accidently uninstalled alot of the clearlooks themes so I need help, after extraction, the themes arent there..Can anyone help?

Are you using the old or new version of FutureLooks?

> **gingin said:**
> does any body had such note from Terminal?
How to solve this?

gin@linux-laptop:~$ emerald --replace

(emerald:6448):GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

What graphics card are you using? Are you using Compiz?

---

### Post by Treeh on 2008-05-25
Nevermind, I figured it out. :)




The theme only appears to be working somewhat....I get some transparency...but it's not a gradient and in my active window it looks like clear looks. Also the minimize/maximize/close buttons don't look right either. Any ideas why?

I'm on Hardy with an Nvidia card...(and a Linux newbie:P)

[IMG]http://img165.imageshack.us/img165/2416/screenshotrq6.png[/IMG]

For larger image: [http://img171.imageshack.us/img171/5356/screenshotwo3.png](http://img171.imageshack.us/img171/5356/screenshotwo3.png)

---

### Post by gingin on 2008-05-25
> **Mazza558 said:**
> Are you using the old or new version of FutureLooks?



What graphics card are you using? Are you using Compiz?

I got  FutureLooks1.0.tar.gz installed
Mine graphics card is ATI mobility radeon 96007/9700
It is laptop computer.

---

### Post by gingin on 2008-05-25
I got FutureLooks1.0.tar.gz installed
Mine graphics card is ATI mobility radeon 96007/9700
It is laptop computer.

---

### Post by sports fan Matt on 2008-05-25
I was trying the old version yet when i extracted it to my desktop as you said in the directions, it said the tar.gz wasnt a valid theme.  I extracted that..and saw what I needed but it still says its not a valid theme for some reason

---

### Post by fickenbaisage on 2008-05-26
> **Treeh said:**
> Nevermind, I figured it out. :)




The theme only appears to be working somewhat....I get some transparency...but it's not a gradient and in my active window it looks like clear looks. Also the minimize/maximize/close buttons don't look right either. Any ideas why?

I'm on Hardy with an Nvidia card...(and a Linux newbie:P)

[IMG]http://img165.imageshack.us/img165/2416/screenshotrq6.png[/IMG]

For larger image: [http://img171.imageshack.us/img171/5356/screenshotwo3.png](http://img171.imageshack.us/img171/5356/screenshotwo3.png)

Did you turn on emerald? If you haven't installed it use the commmand "sudo apt-get install emerald" without the quotes.

After you have installed it, press ALT+F2 and type "emerald --replace" without the quotes to turn on emerald. Then go to System -> Preferences -> Emerald Theme Manager and add the same command under Startup programs to enable it during system startup.

---

### Post by PRGUY85 on 2008-05-26
The Glow theme is not glowing on my Desktop (works on my laptop). Only difference is my Desktop uses 64-bit kernel.

---

### Post by Vinas on 2008-05-27
Not a big fan of this theme at all... Not to be rude but it's just not my style.

---

### Post by Mazza558 on 2008-05-27
> **Vinas said:**
> Not a big fan of this theme at all... Not to be rude but it's just not my style.

Each to their own. What do you prefer?

---

### Post by camelgrass on 2008-05-28
Thank you Mazza, very nice theme, you have talent :).

I was successful installing the original Emerald theme but when I tried to install the other 2 you have for download I get the error message "Error calling tar". I don't think it's a problem with your themes rather Emerald Theme Manager or other system configuration.

Any ideas?

Also with Rainlendar2, I can't start it from desktop or system startup without using "gksudo rainlendar2".

Any help is appreciated, thanks for your effort and sharing.

Cheers,
Marty

---

### Post by Mazza558 on 2008-05-28
> **camelgrass said:**
> Thank you Mazza, very nice theme, you have talent :).

I was successful installing the original Emerald theme but when I tried to install the other 2 you have for download I get the error message "Error calling tar". I don't think it's a problem with your themes rather Emerald Theme Manager or other system configuration.

Try the newest version of the pack, which you'll find in a separate thread in this forum (probably on the second page).

---

### Post by sayakb on 2008-05-28
Aaah.. Finally something fresh.. beautiful.. sleek!!
Great work :D

[ATTACH]71905[/ATTACH]

---

### Post by KrisScofield on 2008-05-29
I can't get the emerald theme to show every time I start up. It just goes back to clearlooks. How do I fix that?

---

### Post by BlackRaven on 2008-05-30
Thanks for the theme.  Got my laptop lookin' all purdy now. :)

---

### Post by Juleshu on 2008-05-30
> **KrisScofield said:**
> I can't get the emerald theme to show every time I start up. It just goes back to clearlooks. How do I fix that?

That question has been asked and answered at least 3 times elsewhere in this thread. Check back a few pages.

---

### Post by Juleshu on 2008-05-30
I like this theme a lot. 
Some comments: To change the panel preferences, you have to right click on your panel then select properties. Pick the background tab, then you can select one of the background images. I'm still waiting for a reverse gradient for top panels. 

Font were hard for me to install. I had to use the command gksudo nautilus in terminal to launch the file manager as root. Then I had to place the fonts in /usr/share/fonts and run the command sudo fc-cache -fv in terminal.

This also apparently lets any user use the fonts.
I also enlarged the fonts a bit to make it easier on my eyes. 

I can't install rainlendar since I'm running 64bit ubuntu. I thought there was a way to run 32bit debs under 64bit ubuntu but I forget the command.

Once you get emerald on, it shows up in system->preferences.
go into terminal and type emerald --replace. This will cause emerald to change the themes. Now you can import the theme you want. 
To make emerald use the theme at startup, go to system-> preferences-> sessions and click add. For name, put emerald. For command, put emerald --replace. For comments you can write in something like "launch emerald on startup" or just leave it blank. That should do it. 



I use AWN on my desktop. It produces a 3d menu on the bottom of the screen that has 3d icons of all of your open windows. I have the options set so the icons bounce when you mouse over them. You can also add launchers to the menu. For instance, if I have azureus as a launcher, I can click on azureus' 3d image to launch it, and once it launches, the icon for azureus now becomes an icon to select it as the active window and maximize it. It's a nice feature and I totally deleted my other panel that shows all of the active windows because I no longer need it.

---

### Post by TommyIndep on 2008-06-07
Hey, I just installed the package and I love this look. I was just wondering, where can I find that blue sea picture you had in one of your screenshots? I just thought that was a very nice wallpaper. Thanks for making this. :)

** I found the pic I was looking for, on page 14. :)

---

### Post by Tuomas on 2008-06-08
> **TommyIndep said:**
> Hey, I just installed the package and I love this look. I was just wondering, where can I find that blue sea picture you had in one of your screenshots? I just thought that was a very nice wallpaper. Thanks for making this. :)

Check post #137 on page 14.

---

### Post by TommyIndep on 2008-06-08
> **Tuomas said:**
> Check post #137 on page 14.

Yeah I noticed, thanks. :popcorn: :)

---

### Post by ispy on 2008-07-09
I have one small emerald problem, it's transparent, but not the right way. screenshot attached.

---

### Post by steveneddy on 2008-07-09
I use this theme's window borders and toolbar background images.

On the focused windows, I made the window borders fade into the desktop.

The unfocused windows have the black outline.

I also made the toolbars a little more transparent in CCSM.

From my personal files:

> 
## [COLOR="Blue"]**make gnome bar true transparent**[/COLOR]

if you are using compiz (desktop effects), you can add true transparency.
go to System->Prefs->Advanced desktop effects settings
Click on General opts.->Opacity settings, and add the following entry at top of the list:
Opacity windows: type=dock
Opacity windows values: 80 (adjust this to your like)

if you don't have the advanced desktop settings util, just install it:

```
sudo apt-get install compizconfig-settings-manager
```

this will make entire panel transparent


---

### Post by prasadz8 on 2008-07-12
[SIZE="4"]**:: THIS IS FOR ALL THOSE WHO WOULD LIKE TO ADD BLUR AND TRANSPARENCY EFFECTS TO THEIR WINDOWS ::**[/SIZE]

[IMG]http://www.deviantart.com/download/90886525/Ubuntu_8_10_LTS___Green_Fling_by_prasadz8.png[/IMG]

the same article is at this [link]("http://prasadz8.deviantart.com/art/Ubuntu-8-10-LTS-Green-Fling-90886525") too.

Make sure you have Compiz Fusion installed.
Terminal:
```
sudo apt-get install compiz compiz-fusion-plugins-extra compiz-extra
```

[FONT="Courier New"]
---------------------------------------------------------------------------
WARNING: You may need graphics acceleration! I'm using a X550 ATI accelerator combined with the latest FGLRX drivers. Blurring and transparency can greatly effect your desktop performance. Anyway, who am I to stop you from experimenting, right?
---------------------------------------------------------------------------[/FONT]

_**How To Make Transparent Windows?**_
1. Open '**Advance Desktop Effects Settings**" under System > Preferences
2. Click '**General Settings**' and then click the '**Opacity Settings**' tab
3. Click '**New**'. A box titled "Edit" pops up.
----Set the opacity slider value to 75%
----Click the '**+**' sign to add a window.
----Play around and experiment with window relations. 'Window Class' is more specific.
----Lastly, click '**Grab**' and hit the window you want to make transparent! Eureka!
4. You can add as many 'New' windows as you like with varying transparencies for each.

[U][B]
How To Blur Transparencies?[/B][/U]
1. Open '**Advance Desktop Effects Settings**" under System > Preferences
2. Enable and click '**Blur Windows**'
----Set '*Alpha blur windows*' = any
----Set '*Blur Filter*' = Gaussian
----Set '*Radius*' = 5
----Set '*Blur Strength*' = 0.5
----Set '*Mipmap LOD*' = 2.5
----Deselect '*Blur Occlusion*'

Note: What I have given above is a sample of how my desktop looks like. You may tweak any of these settings to your own style and the only limit is your own imagination! So explore and invent!

Bhooyakasha, mate!!!
The Linux Kernel rules, spread the word!
muahahahaha!!! =)

---

### Post by Arlanthir on 2008-07-12
@ prasadz8

The only problem is that will make transparent ALL the window and not just the background =/

Fingers crossed for the murrine engine's system and gnome implementing RGBA on all their stuff :(

---

### Post by prasadz8 on 2008-07-12
> **Arlanthir said:**
> @ prasadz8

The only problem is that will make transparent ALL the window and not just the background =/

Fingers crossed for the murrine engine's system and gnome implementing RGBA on all their stuff :(

true... with future development in that section, things will get better... but as for this concoction I've mixed, the illusion of view here is pleasing enough i guess... :)

A dark theme works best with this.

---

### Post by idlefrog on 2008-08-14
> **Mazza558 said:**
> [
**Panel Background**

- Open this folder. Copy the backgrounds to a permanent folder (e.g pictures) and then apply them from the gnome panel preferences.


Ok, I have followed all the other instructions, but I don't know how to do this bit. How do I run Gnome Panel Preferences. I can't find it in any of the menus.

Please could some help.

Thanks.

---

### Post by Mazza558 on 2008-08-15
> **idlefrog said:**
> Ok, I have followed all the other instructions, but I don't know how to do this bit. How do I run Gnome Panel Preferences. I can't find it in any of the menus.

Please could some help.

Thanks.

First of all, you might want to use Futurelooks 2 instead (see signature) as it's easier to follow and has more stuff.

Right-click on your panel and click preferences to solve your problem.

---

### Post by Lord C on 2008-08-15
Nice little pack, thanks for putting it together ^^

---

### Post by jdorenbush on 2008-09-06
Great themes! Thanks for the package.

---

### Post by jobspk on 2009-02-10
Over the past few months, the software and themes I used have enabled me to reach an absolutely fantastic looking desktop, using a combination of natural green wallpapers and themes which fit well together. 

I therefore decided to create a pack with all the files required to get your desktop to look like the attached screenshots.

I don't think this combination is original, but simply a combination of several projects which fit very well together. The theme I seem to have created draws ideas from all 3 Desktop OSs. It has the modern and high-quality style of Apple's Mac OSX, the transparency from Vista (toned down), and the quality of Linux themes, as well as an extremely high-quality font which looks crystal clear at small sizes.

I agree that the screenshot I gave will give you visions of Vista (e.g clock in right-hand corner, the menu I'm using). However, if you decide not to install the menu, you could achieve something like the second, blue screenshot. I don't think this second screenshot looks anything like Vista.


The pack I've created features:
-A modified emerald theme with transparency seamlessly blending into windows. No Vista or OSX theme looks this good.
-Transparent panel backgrounds of your choice
-A small selection of green nature backgrounds reminiscent of OSX Leopard and some Vista wallpapers (They just look good with this theme)
-The beautiful Rainlendar calender, which has just as much functionality as its looks.
-An extremely moddable panel called "Ubuntu System Panel". You're free to try this out, but it requires a bit more effort to fit your tastes.

---

### Post by Trekky0623 on 2009-03-29
I'm currently using your theme.  However, one thing I can't find is the menu bar (File, Edit, etc) in various applications, such as GIMP, for example.  Is there any way to fix this?

---

### Post by sXeChris on 2009-08-01
Can someone link me to the wallpaper in the first screenshot? The one with the ocean and the clouds?

---

### Post by sXeChris on 2009-08-02
Found it; [http://www.desktopnexus.com/dl/inline/57664/1366x768/blue_dock-1920x1200.jpg?nocache=504989](http://www.desktopnexus.com/dl/inline/57664/1366x768/blue_dock-1920x1200.jpg?nocache=504989)

---

### Post by aaron424 on 2009-08-14
Can someone make an installer? I cant get emerald to work

---

### Post by Mazza558 on 2009-08-15
> **aaron424 said:**
> Can someone make an installer? I cant get emerald to work

Hi, 

Futurelooks v1 is over a year old now. You might want to look at Futurelooks 3, the link is in my signature.

---

### Post by jgiacomo on 2009-09-03
Hi everybody !

Where can I find the same wallaper with clouds, sea and bridge ?

Thanks for any answer !
Bye  and thank you for this awesome theme !

---

### Post by topspeeds on 2009-09-22
I cant get emerald to work

[http://methoo.com]("http://methoo.com/")

i tired my luck here

---

### Post by bertmanphx on 2009-09-23
Well,
I could be wrong, but I think Emerald is now deprecated isn't it?

bertmanphx

---

### Post by ubuntuforums on 2009-11-08
I can't get Emerald to work either on 9.10. I guess nobody is replying with any answers?

---

