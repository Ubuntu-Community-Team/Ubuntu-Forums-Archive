---
title: "Gmail notifier"
date: 2005-06-19
forum: General Help
---

### Post by christooss on 2005-06-19
Can I make GNUbiff work with Gmail or is there any of mail notification programs. I know about mail-notification and gdesklets.

---

### Post by Trickyphillips on 2005-06-19
EDIT: Sorry. Nevermind.

Doesn't GMail give POP access?

---

### Post by christooss on 2005-06-19
I konw that

I hate mail-notication. It gives me all kind of erorrs on login. And when I press restart aplication it doesnn't work any more!

---

### Post by Trickyphillips on 2005-06-19
Oops. I think I edited my post while you were writing a response. Sorry.  :?

Have you tried Gnome GTray?

[http://gnome-gtray.sourceforge.net/](http://gnome-gtray.sourceforge.net/)

---

### Post by christooss on 2005-06-20
hm I don't know how to install or start this. Any clues.

apt-get install ruby libopenssl-ruby libgconf2-ruby libgtk2-ruby libgtk-trayicon-ruby

Now what.

---

### Post by Trickyphillips on 2005-06-20
[QUOTE=christooss]hm I don't know how to install or start this. Any clues.

apt-get install ruby libopenssl-ruby libgconf2-ruby libgtk2-ruby libgtk-trayicon-ruby

Now what.[/QUOTE]
 You'll need to download and install [GTray]("http://gnome-gtray.sourceforge.net/gtray-1.3.tar.gz") after installing Ruby (Which you've already done, with the apt-get command).

---

### Post by christooss on 2005-06-20
[QUOTE=Trickyphillips]You'll need to download and install [GTray]("http://gnome-gtray.sourceforge.net/gtray-1.3.tar.gz") after installing Ruby (Which you've already done, with the apt-get command).[/QUOTE]
 Hm

I extracted the file. And then run configure file. Then I run gtray and I get this erorr

gtray: line 2: cd: /usr/local/lib/gtray: No such file or directory

---

### Post by Trickyphillips on 2005-06-20
[QUOTE=christooss]Hm

I extracted the file. And then run configure file. Then I run gtray and I get this erorr

gtray: line 2: cd: /usr/local/lib/gtray: No such file or directory[/QUOTE]
```

$ cd gtray-directory
$ sudo ./configure && make && make install
$ gtray

```

Is this what you did?

---

### Post by christooss on 2005-06-20
I get all kind of errors: permision deniead

And yes I did use sudo

---

### Post by Trickyphillips on 2005-06-20
[QUOTE=christooss]I get all kind of errors: permision deniead

And yes I did use sudo[/QUOTE]
 Hmm. Strange. Chmod the folder and it's contents to 777, and give it another try.

---

### Post by christooss on 2005-06-20
The eroor is 
cp: Cannot make file /usr/local/lib/gtray/TrayIcon.rb`: Permission denied
And all other files in src are listed

---

### Post by kiddyfurby on 2005-06-20
i think the gmail notifier extension for firefox is quite nice~

---

### Post by christooss on 2005-06-20
Yes its quite nice but... I want better :)

---

### Post by Trickyphillips on 2005-06-20
[QUOTE=christooss]The eroor is 
cp: Cannot make file /usr/local/lib/gtray/TrayIcon.rb`: Permission denied
And all other files in src are listed[/QUOTE]

You could try moving them all manually to their respective locations.

---

### Post by jasplund on 2005-06-20
I've enabled pop3 in gmail only because I want to check my account with gnubiff. I used to use mail-notification to check my gmailaccount but it stopped working. also mail-notification doesn't work with SSL. Therefore I had to switch to gnubiff



Johan

---

### Post by oritpro on 2005-06-21
[QUOTE=jasplund]I've enabled pop3 in gmail only because I want to check my account with gnubiff. I used to use mail-notification to check my gmailaccount but it stopped working. also mail-notification doesn't work with SSL. Therefore I had to switch to gnubiff



Johan[/QUOTE]

Yeah, it stopped working for me also. Several times. It would work for maybe a week then out of the blue start crashing consistently. I finally got tired of uninstalling it, manually removing configs, re-installing and re-configuring it. Not worth it, even for free.

Someday, I am going to get myself a Mac.  \\:D/

---

### Post by christooss on 2005-06-22
Can someone tell me hovv to make gmail-notifiy work

I get Preparing to replace gmail-notify 1.6 (using gmail-notify-1.6.deb) ...
Unpacking replacement gmail-notify ...
dpkg: dependency problems prevent configuration of gmail-notify:
 gmail-notify depends on python (<< 2.4); however:
  Version of python on system is 2.4.1-0ubuntu2.
 gmail-notify depends on python2.3-gtk2 (>= 2.2.0); however:
  Package python2.3-gtk2 is not installed.
dpkg: error processing gmail-notify (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gmail-notify

this error

---

### Post by christooss on 2005-06-22
Hm I got gtray (not gmail-notifiy) installed. But... With new servers gtray doesn't work. Does any one has idea what to change.

---

### Post by christooss on 2005-06-24
Do any of you have working gtray?

---

