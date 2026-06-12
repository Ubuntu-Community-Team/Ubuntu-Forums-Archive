---
title: "Gaim's odd formatting"
date: 2005-09-13
forum: General Help
---

### Post by moose6589 on 2005-09-13
Hello, 

I have been using Gaim on Ubuntu for a few months now and have never been able to solve this annoying problem (I don't think I get the problem when I use Gaim on Windows). The problem is: when I am typing some phrase with punctuation at the end (?, !, ", ., etc) and press enter, Gaim puts the messages I send on the right side of the chat window and moves all the punctuation to the left of my message! 

Essentially, if I type "hello?", Gaim will format it so that the window says I typed "?hello", which is utterly confusing to me, even though it sends the right message. With punctuation all over the place, it's hard to concentrate on typing. I will attach a couple screenshots to help explain (excuse my ridiculous GIMP abilities). I'd really love to solve this problem. 

-Richard

---

### Post by Zotova on 2005-09-13
What version of Gaim are you using?

I had problems with the version of gaim which is currently in synaptics - my problem was outgoing transfers simply would not work. To fix this I uninstalled the version of gaim which came with ubuntu and compiled then latest version (1.5.0) from source. This fixed my problem and might also fix yours.

If you didn't want to compile there is also an autopackage available on the gaim website which is similar to a windows installation wizard.

---

### Post by skoal on 2005-09-13
Moose, that's a brain tickler alright. I currently use v1.4 and had no such experiences like that since ~v1.1.  It looks like a possible LOCALE setting, maybe.  I saw no such internationalization settings in "preferences" though.

A quick (and dirty) fix might be to remove the ~/.gaim folder and start over from scratch.  I believe your contacts, buddies, groups and all that for AIM (at least) are stored on their remote server.  Backup the folder first of course.  If that doesn't fix it, then you know your problem lies elsewhere, and it's not gAIM...

\\//_

---

### Post by moose6589 on 2005-09-14
Ok, I tried installing 1.5.0 instead, and I still encountered the problem. Then, I tried deleting my ~/.gaim folder and letting Gaim recreate a new folder. That also didn't work; the problem still remains, with punctuation getting moved towards the front of the message. 

I still suspect the reason for this is because Gaim is moving all messages that I type into the IM window to the right of the screen instead of the left; in essence, it's on right-justify for any messages that I type, except that ending punctuation get moved to the left, not the right. 

I'll attach another 2 pictures of me having a conversation with my other account. The red is messages received from the other account, and the blue is the messages that I type. As you can see, all the blue is in the right side; is there any way to change this? I presume it is not normal behavior as even Gaim's screenshots on the Gaim website do not show this behavior.

---

