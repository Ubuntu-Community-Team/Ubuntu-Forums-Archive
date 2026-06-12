---
title: "how to stop tor"
date: 2006-11-30
forum: General Help
---

### Post by Dr Small on 2006-11-30
Hello. I downloaded tor from the repository using the sudo command, and it installed, and works nicely, but I was wondering how to *stop* it.
Is there some command I run in the terminal or run box to shut it down, or some process?

I'd like to know a simpler way to stop the daemon than shutting the computer down.

Thanks,
Dr Small

---

### Post by LLRNR on 2006-11-30
I don't know what Tor is or what it does, but since you say it's a daemon that you want to turn off at a certain moment, you can try:
```
killall tor
```
If this doesn't do the trick, you can use
```
ps -e | grep tor
```
to see which processes contain "tor" in their name. You'll see their correspondig PID, too, so after you locate the process that controls "tor" you can do:
```
kill -9 PID
```(where PID stands for the numerical value you searched for earlier)

LLRNR

---

### Post by loell on 2006-11-30
maybe this is not the proper way, but i'm just guessing :p 

```
killall tor
```

edit: bah LLRNR beat me :D

---

### Post by j-strap2 on 2006-12-02
To stop the Tor system service gracefully, you should:

```
sudo /etc/init.d/tor stop
```

KDE has a page in the System Services GUI where you can turn services on and off - there must be something similar in Gnome.

---

### Post by Robert.Zapata on 2006-12-09
> **Dr Small said:**
> Hello. I downloaded tor from the repository using the sudo command, and it installed, and works nicely, but I was wondering how to *stop* it.
Is there some command I run in the terminal or run box to shut it down, or some process?

I'd like to know a simpler way to stop the daemon than shutting the computer down.

Thanks,
Dr Small

Howdy Dr:

Not sure if you are using Firefox but check this page:

[http://tor.eff.org/docs/tor-doc-unix.html.en](http://tor.eff.org/docs/tor-doc-unix.html.en)

> 
After installing Tor and Privoxy, you need to configure your applications to use them. The first step is to set up web browsing.

If you're using Firefox (we recommend it), simply **install the Torbutton plugin,** restart your Firefox, and you're all set.


Totbutton plugin here: 
[https://addons.mozilla.org/firefox/2275/](https://addons.mozilla.org/firefox/2275/)

---

### Post by oxyk on 2008-02-27
I'm in real probs with a Tor
I install it, all good, but my Evolution Mail stop to work - Tor don't allow to use pop and smtp - 
I try to kill daemon with /etc/init.d/tor stop
but mail is still don't work
and I still have tor listened ports
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:8118          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:8888          0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN

what I should do to kill it?

---

### Post by Dr Small on 2008-02-28
Try rebooting, but if Tor is stopped, then that is not the problem.

Dr Small

---

### Post by oxyk on 2008-03-01
I reboot the PC, check my firewall rules - pop and smtp open, but evolution still hangs when i try to send email. then I try the kmail - the same problem.
smtp worked before tor and privoxy installation :confused:

then I install postfix + dovecot + squirrelmail and test it
the mail from squirrel goes without any problem! 
now I use thunderbird + postfix and it works ok 
Actually I don't know why evolution hangs with tor, but postfix works

---

