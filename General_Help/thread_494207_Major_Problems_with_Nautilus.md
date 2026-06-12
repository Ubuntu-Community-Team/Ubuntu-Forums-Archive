---
title: "Major Problems with Nautilus"
date: 2007-07-06
forum: General Help
---

### Post by WieboJJ on 2007-07-06
Hi all, I seem to be having a bit of a problem here, and am under the impression that it is nautilus at fault....

      When I start a session Nautilus seems to load, But I can not open any folders. Icons on my desktop seem to freeze, and my right click is gone, but only on the desktop. Nothing from the places menu will run. When I do try to open some thing, such as my home folder, It opens a tab on my window dock, but than closes after about 10 seconds, without actually opening the folder.  All other software seems to be working fine, and I can still access my files through the terminal or other software.

Running $ nautilus in terminal gives me nothing

      I already removed nautilus, rebooted and reinstalled, seemed to have no effect.

      I am running ubuntu 7.04, compiz fusion and xgl, but same problem is in all all sessions, even failsafe.

      Any one have any clue what could be causeing this? Have only found one example of someone who had a problem anywhere close to mine, but he was running gentoo and solved his problem with a simple revdep-rebuild.

     Thanks for your help, as this is obviously quite a pain. Any Suggestions more than welcome.....

---

### Post by colo505 on 2007-07-08
Here's how I fixed the same problem..

In the Terminal
sudo rm -rf gnome gnome2 gnome*

exit
restart

---

### Post by WieboJJ on 2007-07-08
colo505 

Gave what you said a shot, nothing happened, even on reboot.

any other suggestion? what did what you suggested mean?

thanks.....

---

### Post by aysiu on 2007-07-08
Well, a few more tests might help diagnose us the problem:

Have you always had this problem? Or did come recently with the addition of new software?
Have you tried logging in as another user? Does that user have the same problem?
Have you tried installing and using Xubuntu (*sudo aptitude install xubuntu-desktop*)? Does that give you the same problem?

---

### Post by colo505 on 2007-07-09
> **WieboJJ said:**
> colo505 

Gave what you said a shot, nothing happened, even on reboot.

any other suggestion? what did what you suggested mean?

thanks.....

then maybe your gconf settings have messed up..

try 
sudo rm -rf gconf* gnome*
restart

---

### Post by WieboJJ on 2007-07-09
aysiu:

everything was great, part of the problem is I dont seem to be able to figure what had changed, or what I could have done to casue this. That morning I had installed an update from compiz, but as this problem effects all sessions, so It does not seem to have anything to go with my xgl/compiz. I also followed some instructions for improving rendering on sub-pixal fonts.  I tried rolling those settings back and it did not seem to do anything. 

After messing around for a bit going through my history of commands via terminal, somehow i managed to mess everything else up complety....my gnome sessions would no longer load.....I managed to reinstall gnome via failsafe terminal, reinsalled nautilus,  but nautilus still will not run, so i have now installed thunar as my window manager...

Logging in with another User account did not make any diffrence.

As a side note, when I got the majority of my system back up and working after messing up my gnome settings, now on login my desktop wallpaper does not show. This happens for all users. I still have no right click on my desktop, and cannot see any folders/icons on it.

Thunar does not seem to give me access to my network, since I installed it, the shortcut on my "places" has dissapeard.

I will try giving the xubuntu a shot, but am actually a fairly big fan of gnome.

Colo505

Tried what you said, once again seemed to have no effect, even after restart.

again, what did it mean? Im a bit of a noob, but interested in knowing what im putting in my terminal....

once again anyother suggestions are more than welcome....


Thanks for both of your time and help...any info you think I could give that might help pinpoint the problem a little better, just say....

---

### Post by aysiu on 2007-07-09
I have no idea what's going on. It may be fixable, but I think a reinstall might be easier.

---

### Post by WieboJJ on 2007-07-09
Is there anychance Nautilus has a default font or something weird that I may have messed up? going back to the fonts, I had added a new repository and ran

$ sudo apt-get install libfreetype6 libcairo libxft2

is there anyway this was the casue?

---

### Post by colo505 on 2007-07-09
I don't think so.

Frankly, I have no idea why this happens, but it has happens. It happened to me twice, and this is the way I fixed it here. Hope you have already tried removing the gconf and gnome folders together.

---

### Post by WieboJJ on 2007-07-09
remove them from where? do you mean remove the folders altogether? and than do what you said previously? 

thanks again

---

### Post by Bothered on 2007-07-09
I think what is being suggested is that you delete (including all contents) the folders .gnome, .gnome2 and .gconf from your home directory. Have you tried sudo nautilus? If this works, navigate to /home/username/.gnome, delete all contents, navigate to /home/username/.gnome2, delete all contents, and navigate to /home/username/.gconf and delete all contents. I'm cautious about telling you how to do this in command line as misusing rm commands can be disastrous. Note that deleting the contents of these folders will delete all of your gnome preferences (menu, gnome program preferences, etc.).

---

### Post by colo505 on 2007-07-09
here's what you can try again..

System>Preferences>Sessions>Current Session
Uncheck automatically save current session

Open Terminal..

sudo rm -rf gnome gnome2 gnome gnome2_private gconf gconfd

Now restart Ubuntu

---

### Post by WieboJJ on 2007-07-10
Colo505

Deleted .gnome .gnome2 and .gconf
restarted, lost all gnome settings obviously, but that seemed to have fixed the problem.....but than a little bit later the same thing happend. This happend a bunch of times in a row, each time well I modified my desktop, i.e moving icons, panels, switching wallpapers, themes....

I like my text small.....size 7 actually...it almost seems to happen soon after messing with my text....

I will keep messing with it, and will try your last suggestion next time it happens....

thanks again...
\

---

### Post by WieboJJ on 2007-07-10
allright.

Im pretty sure I've narrowed it down to my text. When I change my fonts to size 7 everything goes all to crap, like I said before, with nautilus basically refusing to work. If I keep it at 8, no problems, or at least for now. Stil not sure why, but at least I've got a simple solution....

Thanks Once again for all your help. At least that way I was able to narrow down what I was doing to cause my problems.

funfun

---

