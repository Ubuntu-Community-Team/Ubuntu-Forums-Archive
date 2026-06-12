---
title: "kwallet is driving me nuts"
date: 2008-06-10
forum: General Help
---

### Post by editrix on 2008-06-10
Will somebody please tell me how to assassinate this thing? It keeps asking me for a password for Kmail.

When it first popped up, I told it I didn't want to use it but it refuses to go away. I've tried to configure it (and it's not even on the menu) but no luck.

I've googled it, too, and apparently uninstalling it doesn't help either.

---

### Post by Sinkingships7 on 2008-06-10
Disclaimer: This is a COMPLETE guess. I do not use Kubuntu.

If you don't need it, couldn't you uninstall it with
```
sudo aptitude remove kwallet
```

---

### Post by editrix on 2008-06-11
> **Sinkingships7 said:**
> Disclaimer: This is a COMPLETE guess. I do not use Kubuntu.

If you don't need it, couldn't you uninstall it ...

Thanks for the suggestion, but see my post above. I've found a couple of posts by googling when even uninstalling doesn't work. I suspect that's because there's more than one program or process involved. IOW, there's a special way to uninstall it--or something else--that I don't know about.

Also, it's not a bad idea to use the program for other things, but not for Kmail, where I really don't need it.

---

### Post by lizzard on 2008-06-11
As far as I can remember you can disable kwallet somewhere in kcontrol.

---

### Post by editrix on 2008-06-11
> **lizzard said:**
> As far as I can remember you can disable kwallet somewhere in kcontrol.

You mean the Control Centre? Just searched for Kwallet there and nothing showed up.

I can't find it in the menus either, and 

```
which kwallet
``` returns nothing.

---

### Post by rossmoore on 2008-06-11
Can you see the name of the process driving the pop-up using ps -ef? That could give you a hint of what you need to uninstall / deconfigure. It's not an option in Kmail somewhere, is it? Or could it have fiddled with the launcher for Kmail?

---

### Post by editrix on 2008-06-11
> **rossmoore said:**
> Can you see the name of the process driving the pop-up using ps -ef?

Oh, thanks for this. I didn't know about ps -ef. I suspect it's

```
knotify [kdeinit]
```

Because, for a while I was in Gnome and the process must have triggered, because I saw "knotify" and a couple other words flashing in the panel. Then they stopped.

Only problem is, knotify probably runs all my alarms, reminders, tells me when new mail has arrived, etc.

And "system notifications" has nothing about kwallet.

> It's not an option in Kmail somewhere, is it? 

Nope, nothing that simple, unless I'm blind.

> Or could it have fiddled with the launcher for Kmail?

Not sure what you mean by this. There's nothing in quicklauncher about it.

---

### Post by todak on 2008-06-11
> **editrix said:**
> You mean the Control Centre? Just searched for Kwallet there and nothing showed up.

I can't find it in the menus either, and 

```
which kwallet
``` returns nothing.

Run ```
kcontrol
``` as a command and then look under the heading of Privacy (or Security, I cannot remember which) and there will be a selection for Wallet.

---

### Post by editrix on 2008-06-12
> **todak said:**
> Run ```
kcontrol
``` as a command and then look under the heading of Privacy (or Security, I cannot remember which) and there will be a selection for Wallet.

Woo-hoo! You gave me back the good old Control Centre! Thanks for this. (And why on earth did they take it out?)

Found Kwallet, but _Enable the KDE wallet subsytem_ is NOT checked, and _Prompt when an application accesses an open wallet_ is not checked.

I clicked _Launch wallet manager_ and got an empty box, and a wallet in my system tray.

I found an item in the _Kwallet Handbook_ that says I can "Disconnect an application from the wallet." 

But it appears that I have to have a wallet before I can do that. But when I click on the wallet in my system tray, the box is empty. So I have no wallets to configure.

Aargh!

UPDATE:
Thanks to todak, I was able to even find Kwallet, which has placed a wallet in my system tray. Since then (approx 2 hours), Kwallet has not demanded a password from me. However, I have much better use for the limited space in my system tray so I don't consider this an acceptable workaround.

When I ran kcontrol from the terminal I got this:

> ~$ QComboBox::changeItem: (_defaultWallet) Index 0 out of range

I have no idea if that's significant 

I went off to Launchpad to see if this is a bug but when I searched the bug page:

> There is no project named 'kwallet' registered in Launchpad

However, when you search the Overview page, there's 659 hits for Kwallet.

Surely, it's a bug when a user can't even find a program using standard tools like the Kmenu and "which" from the terminal?

---

### Post by Anlace on 2008-08-09
Just a thought here, take a look and see if KDE is set to open to a saved session.  If it is maybe the saved session used kwallet.  It's a shot in the dark but . . . .

---

### Post by ellgor on 2008-08-09
Hi,
 
When setting up the account and giving your user name and login details there is a box that says "Store POP password" for receiving and "Store SMTP password" for sending, leave them blank, when kontact or kmail start up you will be asked for your password just like login, hope this helps.

Regards, Ellgor.

---

### Post by editrix on 2008-08-10
Wow! Almost 2 months with nothing, then 2 answers in the same day. And it's not even my birthday :-)

> **Anlace said:**
> Just a thought here, take a look and see if KDE is set to open to a saved session.  If it is maybe the saved session used kwallet.  It's a shot in the dark but . . . .

That's exactly what happened. First thing I did after installing was boot up my most used apps, then Save Session. Of course, Kwallet didn't kick in until *after* I'd done that. I had no idea it was running. Sigh!

> **ellgor said:**
> Hi,
 
When setting up the account and giving your user name and login details there is a box that says "Store POP password" for receiving and "Store SMTP password" for sending, leave them blank, when kontact or kmail start up you will be asked for your password just like login, hope this helps.

Regards, Ellgor.

Unfortunately, they are already unchecked. I semi-solved my problem when I realized Kwallet was asking for the ISP's password, not my root password. So now it only pops up once or twice a day. I'd still rather it just went away, though.

Hmm... maybe I'll try storing that POP password.

---

### Post by ElllisD on 2009-11-07
In Kubuntu Karmic Koala I purged kwallet & the next time I logged in, I got a console logon as if I were in runlevel 2, yet autologon engaged after 5-10 seconds at the console, as if kdm were running after all.

Kwallet still running as if it were never uninstalled when KMail sends or receives.

So I uncheck "Save Password" on both IMAP & SMTP accounts, close & reopen kmail, all the way- from the tray.
Then I check mail, enter the password so it can check the mail & check the remember password box.
I send an email & do the same for that, then close kmail- all the way, from the tray.

The next time I start kmail, I hit cancel when kwallet comes up.
At this point KMail asks to store the password itself & I say OK.

I send an email & do the same on that authentication.

Now kwallet seems dead. 
Hallelujah!  

I'd rather be able to really purge it so I didn't have to worry about it coming back- it's like VD!

F&*%@$^ kwallet- annoying *******.

---

### Post by editrix on 2009-11-09
Hi ElllisD:

I'm still using 8.04, and I haven't seen kwallet pop up in I don't know how long--but darned if I can recall how I finally got rid of it. I suspect I did as you did. Anyway, I've copy/pasted your solution into my "howto" directory so it'll be the first thing I try when I upgrade.


> F&*%@$^ kwallet- annoying *******.

Agreed.

---

