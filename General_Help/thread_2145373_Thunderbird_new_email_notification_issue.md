---
title: "Thunderbird new email notification issue"
date: 2013-05-15
forum: General Help
---

### Post by daubotot01 on 2013-05-15
Hello everyone, I just installed Ubuntu 13.04 64 bit on my laptop. I have to check mail frequently so I come up with Thunderbird. But I have an issue now: Thunderbird notifies me with a new email only when it is opening. When I closed it, it does nothing on new email arrival. It seems really strange because I think as an email client it should notify user with new email even when it's not running in foreground (I mean visible to user). Can someone help me to fix this?. Thank you :) (Sorry for my bad English)

---

### Post by gdesilva on 2013-07-10
You may have already found a solution but here is one that works on my 13.04 64 bit Ubuntu Studio with xfce4. If you are not running xfce4 desktop then this may not work.

Add Mail Watcher to your panel.

A good doco on how to configure Mail Watcher applet can be found here [http://spurint.org/files/mailwatch/doc/C/xfce4-mailwatch-plugin.html](http://spurint.org/files/mailwatch/doc/C/xfce4-mailwatch-plugin.html)

In my case Thunderbird is set up to access my Gmail accounts but I did not want Mail Watcher to do polling as well. So, what I ended up doing was to define my mail boxes as mbox mail clients and set the path to ~/.thunderbird/xxxxx.default/Mail/pop.googlemail.com but if you want to be alerted when you are not using Thunderbird then define your mail accounts as pop3 or googlemail accounts and provide the mailbox ids and passwords.

Hope this is useful.

---

### Post by Habitual on 2013-07-10
check out firetray at [https://addons.mozilla.org/en-US/thunderbird/addon/firetray/?src=search](https://addons.mozilla.org/en-US/thunderbird/addon/firetray/?src=search)

---

### Post by gdesilva on 2013-07-10
@Habitual, Tried it out and it works quite well. Thanks.

---

### Post by Habitual on 2013-07-11
Glad it worked out!

---

### Post by gdesilva on 2013-07-13
@Habitual, what is the syntax for playing a music file on arrival of new messages? I tried '/usr/bin/aplay my_music.wav' but the tooltip says that I need to provide the new mail count here. Tried putting 1 as the new mail count in all possible places but cannot get the command working - ie. no sound. The command works perfectly OK on command line.
Thanks

---

