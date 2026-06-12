---
title: "Copy &amp; Paste broken in Ubuntu"
date: 2007-05-24
forum: General Help
---

### Post by sefs on 2007-05-24
Has any one realise this?  That you select some text right click and copy. You close of the window that you copied from go to paste elsewhere and voila ... what you thought you had copied has not been copied.  So you have to reopen what you have copied (this time you are shrewd enough to leave the window open) copy again and paste elsewhere.

Who else experiences this.

This has been the case since breezy.  But now in Feisty it is particularly annoying 3 releases later.

---

### Post by LaRoza on 2007-05-24
If you close the app you are pasting from, it won't paste, at least, for some apps. I think there is something like a clipboard that you can use that would prevent that, but I forget the name. Try searching the forum. 

If the problem is not solved, let us know.

---

### Post by fanatik on 2007-05-24
i understand that its working as designed! i think its gnome that makes it like this. annoying for me too!

---

### Post by tgm4883 on 2007-05-24
It is designed this way.  I forget why and I am too lazy to look it up, but there is a long explanation as to why it is like this.

---

### Post by tgm4883 on 2007-05-24
I lied, im not too lazy.  

[clipoboard specifications]("http://standards.freedesktop.org/clipboards-spec/clipboards-latest.txt") 

Installl glipper

---

### Post by wpshooter on 2007-05-24
> **tgm4883 said:**
> I lied, im not too lazy.  

[clipoboard specifications]("http://standards.freedesktop.org/clipboards-spec/clipboards-latest.txt") 

Installl glipper

Where is this "glipper" ?  I can not seem to find it in Edgy.

Thanks.

---

### Post by tgm4883 on 2007-05-24
google is your friend

Or upgrade to feisty

---

### Post by wpshooter on 2007-05-25
> **tgm4883 said:**
> google is your friend

Or upgrade to feisty

Here is what I see about glipper when I google:

**Please note, glipper is currently under development, beware of bugs and expect much more from future releases. We do not yet have a stable release, and there are currently a couple of known issues with glipper, until our next release you may have to use an older version to get things working smoothly.**

This does not sound like a glowing endorsement to me !!!

And I have tried Feisy and IMO it has too many remaining bugs.  I keep getting these repeating error messages every time I would open the terminal and a beeping sound from the system speaker to go along with the repeating error messages, this behavior continued constantly until I exited the terminal.

Any other suggestions for making copy and paste function work correctly in Edgy/gnome/Ubuntu ?

Thanks.

---

### Post by fanatik on 2007-05-25
...dont close the app before pasting. or use something like xclipboard.

---

### Post by tgm4883 on 2007-05-25
Yea, use xclipboard.  I take it you didn't read the clipboard specifications I posted.  Here, let me do **ALL** the work for you.

> A remaining somewhat odd thing about X selections is that exiting the
app you did a cut/copy from removes the cut/copied data from the
clipboard, since the selection protocol is asynchronous and requires
the source app to provide the data at paste time. The solution here
would be a standardized protocol for a "clipboard daemon" so that apps
could hand off their data to a daemon when they exit. Or
alternatively, [B]you can run an application such as _xclipboard_ which
constantly "harvests" clipboard selections[/B].

In fact, let me ssh into your machine so I can apt-get it for you.


Or alternatively, Don't close the program you copied from

---

