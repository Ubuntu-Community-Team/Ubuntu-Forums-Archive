---
title: "Screensaver does not show up"
date: 2006-10-30
forum: General Help
---

### Post by Ramaddan on 2006-10-30
Hi,

I've been having this weird problem.
It's not really a problem, but more like an annoyance.

When the screen goes into screensaver mode, it locks and everything.

I've set the screensaver to regard the computer as idle after 20 minutes, and the "activate screensaver when computer is idle" option is ticked, as well as "Lock screen when screensaver is active" option.

So all seems fine, and the screen locks and all, and when I move the mouse, it asks me to enter password, but the actual screensaver never comes up.

I tried different screensavers, but the same symptom. Screensaver never really comes up, but aside from that, all other functionalities work fine.

I'm using Ubuntu Edgy, upgraded from Dapper. I did not have this problem in Dapper.

Thanks for your help.

---

### Post by jazzgossen on 2006-10-30
Are you using the beta nVidia drivers and/or Compiz? I had a similar problem with GL screen savers when using Compiz.

---

### Post by JimTDI on 2006-10-30
I'm having the same problem exactly - on a clean install of Edgy.  My video card is an ATI Rage - and I did not have this problem on the prior (Dapper) version of Ubuntu.

---

### Post by pauljwells on 2006-10-30
I get a similar problem - if I use the lock screen function I get the screensaver showing up properly. After a while the monitor goes to sleep and it all goes dark. I can log back in no problem, but any further attempts to lock the screen just give me a blank screen. (In fact the 'Activate Screensaver' checkbox unchecks itself)

It's the same on my PC (pentium) and my mac (G4), so it's something common

---

### Post by Ramaddan on 2006-10-30
Hi,

Hmm... that's kind of sad. Sometimes it's the little things like this which make the difference between getting people to use Ubuntu, or getting people annoyed at Ubuntu.

Did anyone file a bug yet?

This really makes me feel more like taking part in development rather than just complaining, but where do I get started?

I know a bit of C, and a bit of java, and also took a small look at Python. Is there anywhere I can go where it kind of gets me started in making a program for Linux based systems?

---

### Post by lexios on 2006-10-30
Same problem here in Kubuntu 6.10 Edge/Beryl/XGl

I set an opengl screensaver and I can properly test it. It works. Then I enter a 1 minute delay. I wait and instead of the screensaver, the screen goes black (sometimes with a big X on it). If I move my mouse, I get my desktop back with a fade effect...

If there is ever a solution, it would be great to know it.

---

### Post by pauljwells on 2006-10-30
[http://www.ubuntu.com/community/participate/](http://www.ubuntu.com/community/participate/)

:D 

I know a bit of c++ but I've never coded a line of linux! I still try to pass on what little knowledge I have gained from playing with Ubuntu onto those a little back on the learning curve. Amazing community.

I think the slightly buggy release is just a result of a four month (in this case) development cycle. Dapper had a few bugs to start with, but just before I upgraded to Edgy it was sooo totally stable. Edgy will get there too.

---

### Post by autocrosser on 2006-10-30
This is a known problem--Goto GPM (Gnome-Power-Manager) & set Sleep>put Display to sleep>Never & Put Computer to sleep>Never to see if the problem goes away---

I use Xscreensaver--Used 23Meg's guide for Dapper (works fine in Edgy) & went to Sessions & disabled the GPM so they would never run--

That worked for me;)

---

### Post by Ramaddan on 2006-10-30
Ok, I went to Administration->Power Management, and tried your suggestion, but nothing happenec, however, I realized something else.

The tabs have some characters that are not supposed to be there, such as:
<b>Running on AC power</b>

The open and close <b></b> bold enclosures are showing, which might suggest some improper code endings somewhere in the program.

Also, in the General Tab, is the drop down menu "Sleep type when inactive" only supposed to give you "Do nothing" as the only option?

---

### Post by bohne on 2006-11-01
I'm having the same problem on a clean install of Edgy.  I can preview the screensaver with no problem. But when it comes time for the screensaver to kick in, it fades to black and then just sits there, no screensaver is started.  With both GL and non-GL (pic slide show) savers selected.  Move the mouse and it returns to the desktop just like it should.  

I've tried messing around with some of the settings, but it doesn't change anything.  Where are the error log files located for X (or possibly gnome-screensaver / xscreensaver)?  It seems as though the process never gets called to start.  I'm wonder if a 'failed to execute' error might be showing up in a log.

Also which program is responsible for starting the screensaver program? Gnome? X? 

??

---

### Post by gatewayasteroid on 2006-11-01
> **bohne said:**
> I'm having the same problem on a clean install of Edgy.  I can preview the screensaver with no problem. But when it comes time for the screensaver to kick in, it fades to black and then just sits there, no screensaver is started.  With both GL and non-GL (pic slide show) savers selected.  Move the mouse and it returns to the desktop just like it should.  


It's also happening to me, but only every now and then.

---

### Post by Ramaddan on 2006-11-01
Anyone?

I still can't get the screensaver to show up.

---

### Post by wiseguy on 2006-11-01
I tried this...

[http://ubuntuforums.org/showthread.php?t=195557&highlight=Xscreensaver](http://ubuntuforums.org/showthread.php?t=195557&highlight=Xscreensaver)

works for me. :)

---

### Post by timbonz on 2006-11-01
Fresh first time ever never on this partition before install of Kubuntu Edgy and yep same problem, it's these little thing's I though I'd not have to deal with coming from Gentoo... I can test a screensaver but if I leave it the screen goes blank and no saver, no messages in xsession.errors either...

---

### Post by Ramaddan on 2006-11-02
Hi, thanks for all the replies.

Here is an update. I was using automatix to install some programs, so I chose extra fonts, and a couple of other things, like some other video codecs, and things like that, and suddenly, the screensaver works now. ????

Also, Firefox seem to have become more stable, because it kept crashing before, even after using some comon hacks found around the forum, but now it's more stable.

But something else happened now, as I had subtitles showing up before when watching an mkv file, now the subtitles are not showing up again. I'm wondering if all this is font related, but other than that, I'm confused.

---

### Post by Ramaddan on 2006-11-02
Ok, ignore what I said above.

The screensaver is back to not showing up again.
This is very frustrating. And now, the subtitles don't show up to boot, after using Automatix. Who knows, maybe it's not Automatix related.

I'm starting to give up on understanding what's happening, until someone can make sense out of all this for me.

---

### Post by autocrosser on 2006-11-02
Well-I went to my Power management  & it looks normal to me--has three options on the Sleep type tab & no HTML quotes--I'd reinstall Gnome-Power-Manager & anything else that you have as a depend for it--:D  

A note from Matt Zimmerman in a current ubuntu-devel Digest--QUOTE:

Automatix is developed entirely without input from or cooperation with the
development team, and the last time I looked at it, it made some very
questionable modifications to the system which are likely to cause problems
for official packages.  I wrote up some of my findings in the
common-customizations specification.

I cannot recommend the use of this program, and systems where it has been
used cannot be supported with a clean and official upgrade path.




> **Ramaddan said:**
> Ok, I went to Administration->Power Management, and tried your suggestion, but nothing happenec, however, I realized something else.

The tabs have some characters that are not supposed to be there, such as:
<b>Running on AC power</b>

The open and close <b></b> bold enclosures are showing, which might suggest some improper code endings somewhere in the program.

Also, in the General Tab, is the drop down menu "Sleep type when inactive" only supposed to give you "Do nothing" as the only option?

---

### Post by Ramaddan on 2006-11-02
Thanks for the reply. I should keep that in mind now.

Here is another update. When I kill the gnome-screensaver process after system boots, and restart it, then it works fine.

---

### Post by szim90 on 2006-11-02
Although Ramaddan's fix didn't work for me, I found that after purging and reinstalling the gnome-screensaver package, and then rebooting, everything seems to be working fine.

---

### Post by szim90 on 2006-11-03
Nevermind. The problem just started reoccuring after I had my monitor off for a few hours.

---

### Post by puppy on 2006-11-03
Having a similar problem, in that *sometimes* coming out of the screensaver locks the machine, but other times I get the password login and all is back to normal - happens, I dunno, 1 out of 5 times? Strange...

---

### Post by bohne on 2006-11-04
There is a bug report for this subject, it's still unresolved.  

[http://bugzilla.gnome.org/show_bug.cgi?id=355279](http://bugzilla.gnome.org/show_bug.cgi?id=355279)

---

### Post by szim90 on 2006-11-07
They just posted a patch for the gnome-screensaver problem.

[http://bugzilla.gnome.org/show_bug.cgi?id=355279](http://bugzilla.gnome.org/show_bug.cgi?id=355279)

---

### Post by Ramaddan on 2006-11-07
Hi, Thanks for the update.

We cannot apply it though till it is patched at the source level, compiled, and then uploaded to upstream as binary, or else we will have to compile the whole of Gnome Power Manager ourselves, right?

---

### Post by Ramaddan on 2006-11-09
Is this patch going to be applied soon? Thanks.

---

### Post by Ramaddan on 2006-11-14
Hi,

I don't want to be a bother, but how come the patch has not gone upstream yet? Or did I miss something?

Thanks.

---

### Post by AllanP on 2006-11-15
> **lexios said:**
> Same problem here in Kubuntu 6.10 Edge/Beryl/XGl

I set an opengl screensaver and I can properly test it. It works. Then I enter a 1 minute delay. I wait and instead of the screensaver, the screen goes black (sometimes with a big X on it). If I move my mouse, I get my desktop back with a fade effect...

If there is ever a solution, it would be great to know it.

I thought it was something I had done as I am not able to activate the screensaver. No big deal; screen just goes blank. Glad to hear I am not the only one with the glitch. I however, don't have the "X" or the "fade effect".

Regards, Allan

---

### Post by szim90 on 2006-11-17
Has anyone reported this within the ubuntu bug system?

---

### Post by Ramaddan on 2006-11-17
Now that you mention it, don't know.
I know it was reported with Gnome, but if it is not reported with Ubuntu, then they might never realize.

---

### Post by AllanP on 2006-11-17
> **AllanP said:**
> I thought it was something I had done as I am not able to activate the screensaver. No big deal; screen just goes blank. Glad to hear I am not the only one with the glitch. I however, don't have the "X" or the "fade effect".

Regards, Allan

Now it's working. The last two days the scrensaver has been working fine. Hanen't done any upgrades or changes just all of a sudden started working.

---

### Post by smeager on 2006-11-18
Submitted a bug request as this has not been fixed yet.

Bug can be seen here, please validate the bug.

[https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/72280]("https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/72280")

---

### Post by Ramaddan on 2006-11-18
Thanks,
I added a comment to the bug request.

---

### Post by smeager on 2006-11-19
Well according to launchpad a fix has been release. Now I guess its a waiting game until the devs package up the new one and push it out.

---

### Post by NESFreak on 2006-11-22
never mind

---

### Post by Vermyndax on 2006-11-25
Having the same problem here on Edgy.  Here's to hoping they push out that patched release.

---

### Post by oldskoolgamer on 2006-12-03
I was able to resolve this issue on my laptop by installing the kpowersave package from the repositories, works every time like a charm now.8)

---

### Post by Vermyndax on 2006-12-03
Actually, it seems like this has stopped happening to me as of the latest round of updates.

---

### Post by deeptingler on 2006-12-04
mine has been fine over last few weeks and only on new install last night did I get this problem (with gnome) - I used Kubuntu upto last week and had also had the same problem with that too!  strange???

---

### Post by deeptingler on 2006-12-04
ok... Ive just used Synaptic to REINSTALL the gnome-power-manager and gnome-screensaver files (please double check names above) and did a restart.  My "standard" screensaver appeared instead of going "blank" - changed it to a "GL" version screensaver and this is working ok too......   so far so good! :p

---

### Post by zivagolee on 2007-01-15
> **smeager said:**
> Submitted a bug request as this has not been fixed yet.

Bug can be seen here, please validate the bug.

[https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/72280]("https://launchpad.net/distros/ubuntu/+source/gnome-power-manager/+bug/72280")

I was still having this issue but have managed to patch the source and generate a new package and now all is well.  If anyone wants instructions, let me know.. I can post it up.

---

### Post by undertakingyou on 2007-01-15
I'd love if you posted a howto on fixing this issue.  I'm a Noob so you'll have to use small words that are easy to understand :) 
  Thanks!

---

### Post by zivagolee on 2007-01-15
> **undertakingyou said:**
> I'd love if you posted a howto on fixing this issue.  I'm a Noob so you'll have to use small words that are easy to understand :) 
  Thanks!

Ok, hopefully the instructions are good enough.  If you run into any issues, let me know and i'll try to help you out.  Just copy/paste me the error message.

I got the patch from the bug above ([https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/72280](https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/72280)) and the patch is from the gnome bug report ([http://bugzilla.gnome.org/attachment.cgi?id=76106&action=view)](http://bugzilla.gnome.org/attachment.cgi?id=76106&action=view)).  If you want to read thru the bug reports before trying this, it might help you out.  Now onto the howto:

1. create a temporary directory (ie. mkdir gpm)
2. get the source pkg: apt-get source gnome-power-manager
3. cd gnome-power-manager-2.16.1/src
4. use your favorite text editor (ie. vi, nano, gedit) and edit the gpm-manager.c file (ie. vi gpm-manager.c)
4a. starting from line 680, you need to add 4 lines (the + in front of the line means to add those lines):

 			manager->priv->dpms_throttle_id = 0;
 		}
 	} else {
+		/* if throttle already exists then remove */
+		if (manager->priv->dpms_throttle_id > 0) {
+			gpm_screensaver_remove_throttle (manager->priv->screensaver, manager->priv->dpms_throttle_id);
+		}
 		manager->priv->dpms_throttle_id = gpm_screensaver_add_throttle (manager->priv->screensaver, _("Display power management activated"));
 	}
 }

4b.  after you add the above 4 lines (line 2870 after adding the above lines), now you need to add two more lines:

 	/* Do we ignore inhibit requests? */
 	manager->priv->ignore_inhibits = gconf_client_get_bool (manager->priv->gconf_client,
 								GPM_PREF_IGNORE_INHIBITS, NULL);
+	/* set no throttle */
+	manager->priv->dpms_throttle_id = -1;
 }

5. now cd out one directory (ie. cd ..)
6. now to compile and package it up (ie. dpkg-buildpackage -rfakeroot -uc -b)
7. once it's done and you get no errors, cd back out again (ie. cd ..)
8. now to install the package: sudo dpkg -i gnome-power-manager_2.16.1-0ubuntu3.deb
9. restart and that should be it.  configure your screensaver to make sure it starts up, etc in the preferences.

Let me know if you it works for you....

---

### Post by zivagolee on 2007-01-15
Ok, I found a little easier way to patch the file.  You can use #4 above or use this method.  You will need the gpm.txt file below that I just copy/pasted into a file from the patch someone posted on gnome bugzilla.

4. copy the file to the gnome-power-manager-2.16.1/src directory.
4a. patch the gpm-manager.c file: patch -p0 < gpm.txt

Then, continue on with the rest of the steps...

---

### Post by xcarol on 2007-01-17
I had the same problem using Kubuntu Edgy. It has been solved just activating *Power Saving*. That is: *K -> System Settings -> Monitor & Display -> Power saving* Check *Enable power saving* and set *Switch off monitor after* a longer time than the screen saver.

---

### Post by undertakingyou on 2007-01-17
Thanks zivagolee!  Your instructions have proved very good.  I just followed your original step four.  I had two changes that I had to do to get it to work.  First
> **zivagolee said:**
> 
6. now to compile and package it up (ie. dpkg-buildpackage -rfakeroot -uc -b)

I had to do sudo dpkg-buildpackage -uc -b
I don't think that is a big deal.  Worked anyways.  
Second:
> **zivagolee said:**
> 
8. now to install the package: sudo dpkg -i gnome-power-manager_2.16.1-0ubuntu3.deb

The package was gnome-power-manager_2.16.1-0ubuntu3_i386.deb

Other than that your instructions are wonderful!:D   Thanks for your help!!

---

### Post by zivagolee on 2007-01-17
> **undertakingyou said:**
> Thanks zivagolee!  Your instructions have proved very good.  I just followed your original step four.  I had two changes that I had to do to get it to work.  First

I had to do sudo dpkg-buildpackage -uc -b
I don't think that is a big deal.  Worked anyways.  
Second:

The package was gnome-power-manager_2.16.1-0ubuntu3_i386.deb

Other than that your instructions are wonderful!:D   Thanks for your help!!

Sounds good and thanks for the typos :).  Glad I could help!

---

### Post by WKnew on 2007-01-31
I wasn't successful with this how-to, but then I'm new. I already had the edits (additions) that were listed. I tried to complete the how to anyway and got errors. Anyone other suggestions?

---

### Post by undertakingyou on 2007-01-31
What error's did you get?  

UNDERTAKINGYOU--
------------------------

---

### Post by WKnew on 2007-01-31
Thanks to Autocrosser's post, the problem is solved. I thought I had these settings right, but no. The simple things are always the best solution for a beginner.

The post was:

"This is a known problem--Goto GPM (Gnome-Power-Manager) & set Sleep>put Display to sleep>Never & Put Computer to sleep>Never to see if the problem goes away---"

It worked for me also.:)

---

### Post by phenest on 2007-02-09
> **xcarol said:**
> I had the same problem using Kubuntu Edgy. It has been solved just activating *Power Saving*. That is: *K -> System Settings -> Monitor & Display -> Power saving* Check *Enable power saving* and set *Switch off monitor after* a longer time than the screen saver.

I've just tried this and it works! The odd thing is: Power saving doesn't work with my LCD TV. But that I can handle.

---

### Post by Vermyndax on 2007-02-11
Well, I managed to get the package built and installed, but now it takes *forever* to get into GNOME on a fresh boot.  Not sure what the deal is there, but I guess I'll end up having to go back to the regular buggy gnome-power-manager.  I think perhaps that bug is why it's not in general release yet ;)

---

### Post by undertakingyou on 2007-02-12
That's interesting.  I have not had a problem with startup time at all.  Very interesting . . . :confused:

---

### Post by zivagolee on 2007-02-12
same here.  everything works great here..

---

### Post by silverbolt027 on 2007-02-21
I tried and was successful with the installation from the instructions thanks to zivagolee, but it did not solve my problems.

Same problem, where the screen fades out, and nothing comes up.  Sometimes I have distrotion, where parts of the desktop are broken and whatnot....who knows.

I am going to attempt the xscreensaver.

---

### Post by BenBacarisse on 2007-03-11
The patch to gnome-power-manager posted by zivagolee works for me.  Many thanks.  This was driving me mad as I am setting up a laptop for someone else and I want it to "just work".

---

### Post by Michl on 2007-04-24
> **szim90 said:**
> Nevermind. The problem just started reoccuring after I had my monitor off for a few hours.

Yes, exactly, you think you have it fixed, but after coming on once, the problem returns
and instead of a screensaver you get a blank screen.  (And yes, blank screen is not
selected, random screen is not selected -- just to avoid the usual pointless suggestions.)

---

### Post by Michl on 2007-04-24
> **zivagolee said:**
> Ok, hopefully the instructions are good enough.  If you run into any issues, let me know and i'll try to help you out.  Just copy/paste me the error message.

I got the patch from the bug above ([https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/72280](https://launchpad.net/ubuntu/+source/gnome-power-manager/+bug/72280)) and the patch is from the gnome bug report ([http://bugzilla.gnome.org/attachment.cgi?id=76106&action=view)](http://bugzilla.gnome.org/attachment.cgi?id=76106&action=view)).  If you want to read thru the bug reports before trying this, it might help you out.  Now onto the howto:

1. create a temporary directory (ie. mkdir gpm)
2. get the source pkg: apt-get source gnome-power-manager
3. cd gnome-power-manager-2.16.1/src..

Have this problem and am trying to apply the patch, but have some trouble.  First, I already
have gnome-power-manager   (version 2.16.1) installed, but I cannot find any of these
files or folders:

gnome-power-manager-2.16.1/src
gnome-power-manager-2.16.1
gpm-manager.c
gpm-manager.c,v

What file do I edit?

---

### Post by undertakingyou on 2007-04-24
Did you download the source first? ```
 sudo apt-get source gnome-power-manager-2.16.1
```  Once you have it downloaded then you are editing files in there.

---

### Post by Michl on 2007-04-26
> **undertakingyou said:**
> Did you download the source first? ```
 sudo apt-get source gnome-power-manager-2.16.1
```  Once you have it downloaded then you are editing files in there.

Ah, this is the source code and not the application.  Ok, so I did it but this is what happens:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_edgy_main_source_Sources - open (2 No such file or directory)
```

So as far as I can tell nothing was downloaded/
M

---

### Post by Lgndryhr on 2007-06-29
I realize this is an old topic but did not want to make a new one for minor info pertaining to this. There is now a fix for Nvidia graphics card users now. The newest driver that came out June 21st has now allowed all my screensavers to show up and work unlike before. I do not know if this will work for all users. I use a Geforce FX card so anyone with a Geforce FX it will work. Do **_NOT_** install the nvidia-glx driver that Ubuntu offers to install through updates. Uninstall it and install the driver from Nvidia. To uninstall the glx driver and its init scripts use the following code: ```
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-glx-legacy
sudo rm /etc/init.d/nvidia-glx
```

To download the driver that relates to your graphics card go [here]("http://www.nvidia.com/content/drivers/drivers.asp"). 

For more information pertaining to installing the Nvidia drivers go [here]("http://ubuntuforums.org/showthread.php?t=336412") for a step by step process and for help.

---

