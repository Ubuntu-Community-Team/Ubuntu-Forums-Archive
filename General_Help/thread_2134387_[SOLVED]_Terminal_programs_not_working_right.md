---
title: "[SOLVED] Terminal programs not working right"
date: 2013-04-11
forum: General Help
---

### Post by sideburns on 2013-04-11
Right now, I'm trying to help my sister, who runs Ubuntu.  (She's installed Xfce because Unity just doesn't work when you have Parkinson's, but it's not Xubuntu.)  I found some instructions on how to install Google Earth, but they require copying things into a terminal, something she always finds daunting.  (I'm an old-school CLI hack; terminals don't scare me.)  However, if she opens a terminal from the button on the panel, there's no prompt and Paste doesn't work.  Her Applications menu has both Uterm and Xterm.  Neither of them has a menu bar, and right-click does nothing, making Paste impractical.  And, as the commands are rather complex, simply re-typing them isn't exactly doing things the easy way.  If anybody knows how to get the terminals to work, or at least how to find out why they don't, we'd both appreciate it.

---

### Post by nerdtron on 2013-04-11
> Paste doesn't work.
> making Paste impractical
> If anybody knows how to get the terminals to work, or at least how to find out why they don't, we'd both appreciate it.

She can do Ctrl+C to copy the commands from your email, chat, instant message or document or etc. and open a terminal window and press

CTRL+SHIFT+V      ---------->   this key combination is "paste" in the terminal.




EDIT: sorry about my post, it only works on the terminal and not on Uterm and Xterm.

EDIT AGAIN: This link tells you how to paste in xterm by using the middle click button [http://www.linuxquestions.org/questions/linux-software-2/copy-paste-in-xterm-130077/](http://www.linuxquestions.org/questions/linux-software-2/copy-paste-in-xterm-130077/)

---

### Post by Impavidus on 2013-04-11
I don't think you need a terminal to install google earth. Just download the .deb file from [http://www.google.com/earth/index.html](http://www.google.com/earth/index.html) (click download. I didn't paste the final link because it redirects you to a localised page). If you access the site with your Ubuntu machine it gives you the .deb option. Double click the .deb, give your password and it should install.

The latest version has given problems. Maybe these are solved now, else use the advanced settings and download the older version.

---

### Post by sideburns on 2013-04-11
Where in the terminal do I paste it, Nerdtron, when there's no prompt.  (I know that I mentioned that; I just looked.)

And, Impavidus, I'm trying to set things up so that she won't have to use a terminal again, because, as I also mentioned, she's intimidated by it.

---

### Post by Impavidus on 2013-04-11
Then don't use the terminal. Download the .deb, double click it and it will open in the software centre. Click install, give the password and it installs. I think there will appear an entry in the xfce menu. If not, you can add it manually (make an entry pointing to the command "google-earth"). No need for scary terminals, she can start google earth by clicking in the menu.

Where did you find those instructions on installing google earth? They sound overly complicated. It's just three mouse clicks and a password.

That being said, if you do some of her system administration and love terminals, it would be good to get them operational again.

---

### Post by sideburns on 2013-04-11
I thought I'd explained why we want to do it this way, but I see that I didn't.  If we install the special repo, any and all updates to Google Earth get installed any time she updates her system.  It's a little more work now, but it makes things easier later.

In regard to your final comment, I only get involved when it's something she can't handle, or doesn't know how to do.  Most of the time, if it requires a terminal, I do it, but I was hoping that since this should be nothing more than copy/paste, she could do it herself and maybe get a little more comfortable with a CLI.  And yes, we do need to get at least one of the terminal programs working correctly, because there are times that I need it and using ^Alt-F3 (as an example) to get to at TTY isn't appropriate because I need to see something in an email, or on a webpage while I'm working.

I guess that if push comes to shove, we can always copy/paste the commands into an editor, with #!/bin/bash on the first line and save it.  Then, use chmod to make it executable and run it with sudo.  (If I'm doing that, of course, I'll remove that from the commands.)  That can be done from an alternate TTY because I won't actually need to copy or paste anything at that point.  Still, it does sound like giving up, doesn't it?

---

### Post by Habitual on 2013-04-11
> **sideburns said:**
> Where in the terminal do I paste it, Nerdtron,...Classic!

---

### Post by sideburns on 2013-04-11
I'm not sure what you mean, because when we open up the terminal from the panel, there's no prompt, no menu bar and right-click doesn't allow for paste.  If all I get is a blank window that doesn't respond, I ask again:  WHERE DO I PASTE IT?

---

### Post by sideburns on 2013-04-11
Don't be more absurd than you have to be.  Reinstalling simply because the terminals aren't working right is the Microsoft "solution."  In case you haven't noticed, this is a Linux forum.

---

### Post by howefield on 2013-04-11
In xterm, try Ctrl + Shift + Insert to paste.

---

### Post by steeldriver on 2013-04-11
OK so out of curiosity I just went ahead and installed xfce4 on top of my Ubuntu 12.04, and fired up an xfce4-session - and my terminals also appeared broken

Turns out they *are* functioning - just the default color scheme is back text on black background (very Hotblack Desiato). If that's the same issue for your sister's setup then there is a simple fix:

1. go to the terminal's 'Edit' menu and select 'Profile Preferences'

2. Choose the 'Colours' tab

3. uncheck 'Use colours from system theme'

In my case that instantly changed the terminal back to black text on a white background. Hope this helps.

---

### Post by sideburns on 2013-04-11
I passed this on to my sister, and she's reported that it worked.  Color this thread [SOLVED!]

---

