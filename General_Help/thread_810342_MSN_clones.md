---
title: "MSN clones"
date: 2008-05-28
forum: General Help
---

### Post by yc2 on 2008-05-28
Hi,

After having used Ubuntu for a little more than a year I am very satisfied. I have also tried to learn a little about computers from the forums.

One of the few things that still makes me start up the Windows partition is MSN. (Some of my friends use MSN.) I know very little about Linux MSN clones.

Could you please tell me which clone is "best"! Or maybe quickly tell me which pros and cons they have?

What is most important for me is:
1. It should accept input from SCIM (I most often chat in Chinese)
2. I want to be able to enter the short message that my contacts can see beside my name.
3. Voice dialogue should work OK
4. If possible file transfer speed should also be "OK"

Thanks a lot for advice.

/yc2

Sorry if I posted on the wrong board. Ubuntuforums.org is fantastic, but I sometimes don't find the right board. (My fault ;)

---

### Post by Grognot on 2008-05-28
[Amsn](http://www.amsn-project.net/) is probably as clonish you'll get on Linux.

---

### Post by yc2 on 2008-05-28
> **Grognot said:**
> [Amsn](http://www.amsn-project.net/) is probably as clonish you'll get on Linux.
Thank you.
Synaptic - one click - enter my e-mail and pwd. After that everything is running smoothly. Ubuntu is really making ground fast.

The small message beside my name can be entered (my personal compulsion ;)
SCIM can be used for input.

I am really happy and impressed. Now my friends can "see me" on their desktops, that is the most important thing.

However, as I understand, voice communication is not supported (but video is). **So I guess the best thing is to go to Skype homepage and download Skype 2.0 for Linux ??** My friends will probably accept installing Skype (if they haven't already).

---

### Post by danwood76 on 2008-05-28
It is possible to compile aMSN with audio chatting:
[http://www.amsn-project.net/forums/viewtopic.php?t=4799&highlight=](http://www.amsn-project.net/forums/viewtopic.php?t=4799&highlight=)

It depends how confident you are with compiling apps.

Also with regards to 4. above, you can set the port that MSN uses for file transfers, if you open that port up in your router aswell your msn file transfer speeds will be really fast.
Accross my LAN I had full bandwidth file transfers to my friend with aMSN.

-- edit --

I havent managed to read how far the audio has got in the svn branch but I assume its further than the post above (we're now a few months on)

---

### Post by Zorael on 2008-05-28
I much prefer [emesene](http://emesene.org/) over Pidgin and aMSN. There is no voice chat nor camera support, though. SCIM inputs fine.

And file transfers are sent directly (and not through the server like pidgin does/used to), so they're as fast as your connection can make them.

---

### Post by AndyCooll on 2008-05-28
There's also Emesene. Never used it but I believe it's a good MSN clone.

And Kopete, although not an MSN clone since it's the KDE IM tool, offers all of those features and more.

:cool:

---

### Post by yc2 on 2008-05-28
**_Thank you everyone._**

**_Regarding danwood76's suggestion:_**
Skype went equally nicely into the system, but of course it would be easier for my friends if I could run audio through the same program (aMSN). I am reasonably familiar with compilation (mostly on pdp-11 though ;)) but I do not know so much about dependencies. (I should maybe run partimage for backup before proceeding.)

This is what I need according to the link:

```
1 - glib 2.14 or newer

2 - gstreamer 0.10.17 or newer

3 - gst-plugins-base 0.10.17 or newer

4 - gst-plugins-good 0.10.7 or newer

5 - gst-plugins-bad 0.10.6 or newer

7 - gst-plugins-farsight - 0.12.8 or newer

8 - farsight2 - 0.0.2 - NOT git and NOT newer

 Note For ubuntu gutsy users, you can have all those dependencies (apart from glib) by downloading them as .deb files at : http://people.collabora.co.uk/~kakaroto/gutsy-debs/

Once you install (compile) all of these dependencies, you will need to get the latest SVN version of aMSN (revision 9729 or newer) and compile it :

 ./configure

This should tell you if the dependencies were correctly installed. If it is, then type :

 make

You are now ready to make an Audio Call. 
```

I get most packages through synaptic, but I cannot find glib and farsight2. (In synaptic I find glibc source and I find the farsight webpage but no download)

For the moment I have no router, so I guess I don't have to do anything, I will get maximum speed from the filetransfer immediately?

**_Regarding AndyCooll's suggestion:_**

I have not used Kubuntu before. But the way to immediately get a "full" MSN client including voice-support (Kopete) is to first install KDE? I have no background to form opinion in this field, but I have been so happy with gnome+terminal for the time I have used Ubuntu. Why must i go to KDE? Here I also fear the dependencies, but if there is no other way I will install KDE.

Is there anything ""bad"" that can happen if I go from Gnome to KDE? Compiz-fusion works well right now. Is there a good guide for KDE install?

Thanks for all advice. Already good result: My friends can see my MSN on their desktops and Skype installed well to be used when needed.

---

### Post by danwood76 on 2008-05-28
You can install kopete without KDE, it just installs a load of KDE libs aswell.
aMSN installs a load of extra libs aswell because its not GTK.

I used to use Kopete for video chat last year.
Its probably a lot easier than recompiling aMSN as it looks like it has some odd dependancies to get it working.

---

### Post by yc2 on 2008-05-28
Thanks for continued help.

aMSN seems to work well, also supports the "essential" off-line-message. (Only sometimes long wait before you can type.)

Kopete installed well. However, some problems using it. When I go from off-line to one of the online status options it shows the contacts that are on line in a different color. So obviously it knows that they are on-line. However, if I click one of the contacts that are on line it says something like: "You cant contact this person, he/she is off line". (But the very first time I tried it was possible. I have also tried changing my own status. Restarting computer etc.)

Maybe Kopete runs better w. KDE? I also think there is no voice option in Kopete?

(Maybe I should not un-install Kopete, there is still space on the disk, I didn't make image-backup before the install. I suffer from "dependency-paranoia" ;) )

So, for the time being I think I try aMSN (and Skype for audio) and gradually see if I can udnerstand the aMSN dependencies for audio.

Thanks.

---

### Post by AndyCooll on 2008-05-29
> **yc2 said:**
> **_Regarding AndyCooll's suggestion:_**

I have not used Kubuntu before. But the way to immediately get a "full" MSN client including voice-support (Kopete) is to first install KDE? I have no background to form opinion in this field, but I have been so happy with gnome+terminal for the time I have used Ubuntu. Why must i go to KDE? Here I also fear the dependencies, but if there is no other way I will install KDE.

Is there anything ""bad"" that can happen if I go from Gnome to KDE? Compiz-fusion works well right now. Is there a good guide for KDE install?

Thanks for all advice. Already good result: My friends can see my MSN on their desktops and Skype installed well to be used when needed.
As you should have found when using Synaptic, it will automatically install any KDE dependencies it needs. You don't have to go through the process of installing the whole of KDE itself. And Kopete, just like most KDE apps, works fine with GNOME (and the same can be said of GNOME apps with KDE).

And although I haven't used Kopete for ages, IIRC it *does* have audio support.

:cool:

---

### Post by Josh08 on 2008-05-29
emesene is a fantastic msn clone. It fits in with ubuntu themes and plus you can send ulimate nudges which on normal msn you cant. And i think (im not sure about this) but i think your "personal message" can be as long as you want it to be. Like on the actual msn messenger itself it limits you to a certain ammount of words but with emesene you can type as many as you like i'm pretty sure. It supports multi-convo's, emotions, send/recieve files, it's awesome. Emesene all the way hahaa :KS

---

