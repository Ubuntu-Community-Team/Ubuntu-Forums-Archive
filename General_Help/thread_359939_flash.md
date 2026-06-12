---
title: "flash"
date: 2007-02-12
forum: General Help
---

### Post by Lowfront on 2007-02-12
alright now I have had ubuntu for over 3 months now and still have not got flash working.  I have tried every tutorial there is.  Now as of right now it seems like some things work and some don't.

For instance It seems like I can get flash chat rooms working and utube clips that are right on a forum thread.  

But I cant just search on utube and watch movies.

---

### Post by taurus on 2007-02-12
Have you tried this one, yet?

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by r4ik on 2007-02-12
Did you try this one ?

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by r4ik on 2007-02-12
:)

---

### Post by Lowfront on 2007-02-12
Yes.

I think I remember everything going fine till this part

sudo mv install_flash_player_9_linux/libflashplayer.so /usr/lib/firefox/plugins/
sudo mv install_flash_player_9_linux/flashplayer.xpt /usr/lib/firefox/plugins/
These commands move the Flash plugin to the appropriate plugins folder.

rm install_flash_player_9_linux.tar.gz

---

### Post by r4ik on 2007-02-12
Just move to the next line.

---

### Post by Lowfront on 2007-02-12
lowfront@lowfront-x60:~$ rm install_flash_player_9_linux.tar.gz
rm: remove write-protected regular file `install_flash_player_9_linux.tar.gz'? y
lowfront@lowfront-x60:~$ rm -r install_flash_player_9_linux
rm: descend into write-protected directory `install_flash_player_9_linux'? y
rm: remove write-protected regular file `install_flash_player_9_linux/Readme.txt'? y
rm: cannot remove `install_flash_player_9_linux/Readme.txt': Permission denied
rm: remove write-protected regular file `install_flash_player_9_linux/flashplayer-installer'? y
rm: cannot remove `install_flash_player_9_linux/flashplayer-installer': Permission denied
lowfront@lowfront-x60:~$

---

### Post by Maestro23 on 2007-02-12
You can make it easy on yourself if you get the flash-plugin from the repositories. Use Synaptic(GUI) or apt-get(command line).

Called "flashplugin-nonfree"

Unless you are using this as a learning thing for installing by command line and source.

---

### Post by Lowfront on 2007-02-12
Believe me I know that and automatix doesn't work.

---

### Post by jackrobinson on 2007-02-12
> **Lowfront said:**
> Believe me I know that and automatix doesn't work.
if automatix doesnt work, report to [http://www.getautomatix.com/forum](http://www.getautomatix.com/forum) and report exactly whats going wrong. They will help you.

---

### Post by ahaslam on 2007-02-12
Download the .tar.gz & follw the given directions: [http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Tony.

---

### Post by r4ik on 2007-02-12
So there are some things that can't be removed.
Have you restarted firefox and see if it works ?

---

### Post by Lowfront on 2007-02-12
> **Anthony Haslam said:**
> Download the .tar.gz & follw the given directions: [http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Tony.

that file on there doesn't want to download

---

### Post by Lowfront on 2007-02-12
> **r4ik said:**
> So there are some things that can't be removed.
Have you restarted firefox and see if it works ?


of course...doesn't work

---

### Post by Maestro23 on 2007-02-12
> **Lowfront said:**
> that file on there doesn't want to download

I was just there and it d/l for me.  What version of Ubuntu are you running? 32 or 64-bit?

---

### Post by Lowfront on 2007-02-12
32 bit

---

### Post by Maestro23 on 2007-02-12
> **Lowfront said:**
> 32 bit

Hmm... Does it give you an error when you left-click it and try to download it?

---

### Post by Lowfront on 2007-02-14
It just doesn't want to download.  Sticks at 1% downloaded.

[http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Can someone please download that  tar.gz file for me and send it to me via email

---

### Post by Maestro23 on 2007-02-14
> **Lowfront said:**
> It just doesn't want to download.  Sticks at 1% downloaded.

[http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.defytherules.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Can someone please download that  tar.gz file for me and send it to me via email

[email]lowfront@gmail.com[/email]

Thanks so much.

Check your email.

---

### Post by Lowfront on 2007-02-14
alright thanks so much for that.

Now I'm kind of stuck on a simple direction.

# Unpackage the file. A directory called install_flash_player_9_linux will be created.
# In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).





How would I navigate to this directory in the terminal?

---

### Post by Maestro23 on 2007-02-14
> **Lowfront said:**
> alright thanks so much for that.

Now I'm kind of stuck on a simple direction.

# Unpackage the file. A directory called install_flash_player_9_linux will be created.
# In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).





How would I navigate to this directory in the terminal?

cd = change directory

Where did you d/l the file to: home ? Desktop?

cd /home/username/Desktop

Then type: ls = list the files in the current directory.

pwd = will tell you your current directory you are in.

Good site to get your feet wet with commands/file structure: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Good luck.

---

### Post by Lowfront on 2007-02-14
alright well I said that it installed.  

But it still isn't working.

Did it maybe install into the wrong directory?  Can't I assume that it would install into the right directory?

Is there somthing I need to do with firefox to get it working?

---

### Post by Maestro23 on 2007-02-14
> **Lowfront said:**
> alright well I said that it installed.  

But it still isn't working.

Did it maybe install into the wrong directory?  Can't I assume that it would install into the right directory?

Is there somthing I need to do with firefox to get it working?

Did you restart firefox after you installed?

Naviate to /usr/lib/firefox

cd /usr/lib/firefox
ls

Should see a plugin directory there. All plugins are kept here for firefox.

This is what is in my /usr/lib/firefox/plugin:

> flashplayer.xpt        mplayerplug-in-gmp.xpt  mplayerplug-in.so
libflashplayer.so      mplayerplug-in-qt.so    mplayerplug-in-wmp.so
libjavaplugin.so       mplayerplug-in-qt.xpt   mplayerplug-in-wmp.xpt
libunixprintplugin.so  mplayerplug-in-rm.so    mplayerplug-in.xpt
mplayerplug-in-gmp.so  mplayerplug-in-rm.xpt


Should have libflashplayer.so in there.

---

### Post by Lowfront on 2007-02-14
hmm... idk 

its in there...

but not working

---

### Post by Lowfront on 2007-02-14
could that possibly be a bad file in there from a previous attempt at an install?

---

### Post by Lowfront on 2007-02-15
?

---

### Post by crossedout on 2007-02-15
Hey Lowfront,

I'm not sure that I can be of greater assistance than the information that's already been given, but I do have a thought.

Type about : plugins (no spaces) in the address bar of firefox.
Look for an entry titled "Shockwave Flash".  There should be only 1 listing and there should be only 1 entry of libflashplayer.so.

If there are more than 1 entry, you'll need to remove all but the one you want to use.  I will assume its v9, so remove all the others if you have them.  Having a conflict is my best guess as to why you are having trouble.  I hope that helps.

-Xout

---

### Post by RuarriS on 2007-02-15
also if you're getting the "permission denied" warning, then you should use "sudo ...";

ex. 

sudo rm install_flash_player_9_linux.tar.gz

---

### Post by Lowfront on 2007-02-15
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by Lowfront on 2007-02-15
Its wierd because it seems like some flash things work and others don't.  For instance.

I can watch a video off of utube if its posted right onto a message board.  Meaning the video is in the message board post.  But I can't browse utube.

And it seems like I can open certain flash chat rooms.

But must flash things I can't use at all.  Like flash based private message systems, or flash on websites like my bank or credit card or anything like that.

---

### Post by Lowfront on 2007-02-16
??

---

### Post by Lowfront on 2007-02-19
Well after months of trying to get flash to work.  Some how it is all of a sudden working.


I don't know what happened but I didn't even do anything since my last attempt that didn't work.

I don't know but ubuntu no has a mind of its own on my notebook.

Thanks ubuntu for granting my wish for flash!

---

