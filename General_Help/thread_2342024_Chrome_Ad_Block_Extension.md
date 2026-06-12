---
title: "Chrome Ad Block Extension"
date: 2016-11-03
forum: General Help
---

### Post by ray42 on 2016-11-03
Have one or two extensions in chrome 3 at present. Pinterest Save Button, WorkFlowy and a password manager

I did have AdBlock but it froze and crashed Chrome.

What is a good advert blocker? Is there another way, other than an extension?

---

### Post by howefield on 2016-11-03
> **ray42 said:**
> I did have AdBlock but it froze and crashed Chrome.

Give uBlock Origin a go.

> What is a good advert blocker? Is there another way, other than an extension?

Slightly left field and probably not what you were thinking but Opera browser has a built in ad blocker which seems pretty decent, and can run Chrome extensions as I understand it.

---

### Post by ray42 on 2016-11-03
I do like Opera, hmmm, interesting.

My password manager works, so far, so good.

I know it is based on the same engine as Chrome? Yes?

Is there anything I would be missing out on if I swapped to Opera?

---

### Post by howefield on 2016-11-03
> **ray42 said:**
> I know it is based on the same engine as Chrome? Yes?

As far as I am aware, yes.

> Is there anything I would be missing out on if I swapped to Opera?

Impossible to answer for someone else but personally I find nothing to miss in a comparison with Chrome, although my needs are reasonably simple.

I use Opera sync to do all the syncing that I used to use a google account for syncing on Chromium/Chrome and relatively few extensions.. Ghostery, uBlock Origin (although built in ad blocker is also switched on), Violentmonkey and Noscript Suite Lite. 

Easy enough to install and test out, and uninstall if not suitable :)

---

### Post by ray42 on 2016-11-09
Yes Opera great. Even lets me install Passwordbox (best password manager in my opinion).

Where have the minimise and maximise button gone?

---

### Post by CantankRus on 2016-11-09
I use opera and my favourite security extensions are umatrix and History Eraser.
Use [**Download Chrome Extension**]("https://addons.opera.com/en-gb/extensions/details/download-chrome-extension-9/") to install extensions from Google Chrome Web Store.

---

### Post by Frogs Hair on 2016-11-09
Opera has a pretty diverse extensions page of its own . Been testing the built in adblocker and VPN on the beta build. I use a password manger as well.

---

### Post by ray42 on 2016-11-10
What password manager do you use as Passwordbox is due to end in December?

---

### Post by howefield on 2016-11-10
> **ray42 said:**
> What password manager do you use as Passwordbox is due to end in December?

Don't know Passwordbox but I use Keepassx which is in the repositories. I sync the database to several devices with an owncloud setup. Please start a new thread if you want a discussion on password managers.

---

### Post by CantankRus on 2016-11-10
Don't like using browser extensions for password management.
Just use keepassx and use megasync to sync the keepassx file to phone.
For sites that are not that important security wise, after saving in keepassx 
I also let the browser save the password to the login keyring.
Keepassdroid can open  keepassx data bases on android phones.

---

### Post by ray42 on 2016-11-10
> **CantankRus said:**
> I also let the browser save the password to the login keyring

How do I use the login keyring, what does it do?

---

### Post by CantankRus on 2016-11-10
> **ray42 said:**
> How do I use the login keyring, what does it do?
You don't have to do anything except save your password when asked.
The login keyring is used by chrome/opera browsers to store passwords whenever
you confirm for it to save a password.
I'm using opera-beta and I think the default setting is to ask to save passwords.
opera://settings > privacy and security > passwords
In opera-beta there is also an option to manage saved passwords.

The login keyring can only be unlocked from within your graphical Gnome xsession.
It is unlocked when you login at the greeter.
If you use autologin, the  login keyring is not unlocked so when you open
your browser you will be asked to provide your admin password to access passwords.   

The encrypted file that gnome-keyring unlocks and where the browser saved passwords are stored is ~/.local/share/keyrings/login.keyring
I backup and copy this file over to new Ubuntu installs and it is unlocked at login if the same password is used as previously.
I also save the passwords in keepassx. It's just more convenient to let the browser fill in passwords rather than opening keepassx.

For sites where you should be more security conscious (banking, paypal etc), I only store the passwords in keepassx and use new private windows to login.

---

### Post by ray42 on 2016-11-11
OK that's great.

So the keyring then logs you in automatically to these sites with the saved password?

---

### Post by CantankRus on 2016-11-11
Yes. Passwords are saved in the keyring with a corresponding "action_url".
When you open that url in the browser, the login fields will be filled in.

---

