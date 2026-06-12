---
title: "Skype for Linux...just freezes?"
date: 2018-02-17
forum: General Help
---

### Post by goemonburo on 2018-02-17
Something's happened recently to my Skype for Linux.  I'm running Ubuntu 16.06LTS.  It used to work fine.  Haven't upgraded hardware or anything like that but recently it just repeatedly hangs.  

The process is exactly this:

1.  I select "Skype" from the application menu.
2.  It flashes a message saying "You've been signed out of Skype, launch the application to sign back in" (with a 'View' button).
3.  The login screen appears.
Up to this, no worries.
But when I log in, nothing happens...the Skype window stays white, never loads any of the dial options or my chat messages, etc., and it just sits there.

I've installed and reinstalled via apt-get, and I've even tried to use the direct one from the Skype website.  8.15.0.4  They are the same.  

I sleuthed around and don't see lots of people having this issue so perhaps I'm searching wrong or maybe it's just me.  Anyone know what's going on?

Thank you!

---

### Post by HermanAB on 2018-02-17
MS changed the Skype protocol.  You need to change to something else, e.g. Viber.

---

### Post by goemonburo on 2018-02-17
Wait, so Skype no longer works for Linux?  At all?  Did I miss a memo?  

(Why do they still have it there on their site, then?)

Can Viber access my Skype account and so on?  Or do I just plan on Skype on my Android phone from now on?  

(Kind of surprised I haven't seen massive outcry about this if indeed they just axed the entire Skype for Linux...kinda thinking there's something else going on.)

---

### Post by Autodave on 2018-02-17
That actually happened a couple months ago and there were tons of posts about it.

---

### Post by goemonburo on 2018-02-17
Weird, as this worked fine until a week or two ago...seems like the major shift happened last fall?

---

### Post by deadflowr on 2018-02-17
Try the snap version.
```
sudo snap install skype --classic
```
More: [https://insights.ubuntu.com/2018/02/13/skype-discuss-easing-linux-maintenance-with-snaps/]("https://insights.ubuntu.com/2018/02/13/skype-discuss-easing-linux-maintenance-with-snaps/")

---

### Post by ajgreeny on 2018-02-17
Skypeforlinux still works fine but is now very different from the very old version 4 from a matter of only months ago.

Download the .deb file direct from the Microsoft site at [https://go.skype.com/skypeforlinux-64.deb](https://go.skype.com/skypeforlinux-64.deb) and install it with gdebi (or sudo dpkg -i) and it will add the repos tpo your software sources and keep it updated.

You may find, as I do, that selecting the start minimised to the panel opens an empty and inactive window which you can overcome by disabling the start minimised option, letting it start to an active window, then minimising to the panel.

---

### Post by goemonburo on 2018-02-17
@ajgreeny, thank you yes, it is opening a blank, inactive window.  But I don't know how to get to the Settings -- they are greyed out when I'm in the initial signin page, as are most of the other options.  Then after I log in, it's blank and the Preferences and other options (including even the Skype version) are greyed out.  Going to the toolbar icon and selecting "Open Skype" doesn't do anything either.  Can I access a config file perhaps and manually edit that setting?

---

### Post by ajgreeny on 2018-02-18
Try renaming the ~/.config/skypeforlinux folder in your home as a backup after first shutting down skype completely, then restart skype.

That will start skype with default settings which may get you back to something you can work with and change settings to what you now need.

---

### Post by goemonburo on 2018-02-19
Thanks @ajgreeny -- closed out of Skype, did ps aux | grep skype to make sure all processes were shut down, renamed the file, then restarted skype...

...and it was the same thing.  A non-operational white window with most of the options grayed out, and a toolbar icon in the lower right corner that doesn't do anything.

Still scratching my head.

---

### Post by goemonburo on 2018-02-19
Not scratching my head anymore:  it's working.  But I had to completely shut down the computer.  Not sure what that did, perhaps there are processes that don't have "skype" in them that never got closed properly?  But when I did shutdown (after renaming the .config as you suggested), and restarted it finally worked again.  #hatewhenlinuxactslikewindows  #butifitworksI'mhappy

So...I'm all set.  And I don't know what the posts about it NOT working above are.  It works fine now.  Fingers crossed, this issue won't reappear.  If it does, is there a way to get a full list of the running processes Skype spawns so that I can shut them all down and not have to reboot?

Thanks again for all the help!

---

### Post by ajgreeny on 2018-02-20
Great news! I the hope that this continues to work for you, please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

