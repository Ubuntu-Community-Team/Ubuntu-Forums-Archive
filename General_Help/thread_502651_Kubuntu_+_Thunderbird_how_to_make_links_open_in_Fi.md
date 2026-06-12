---
title: "Kubuntu + Thunderbird: how to make links open in Firefox?"
date: 2007-07-16
forum: General Help
---

### Post by anachreon_ on 2007-07-16
Hello,

I can't for the life of me figure out how to make internet links in an email, while using Thunderbird, open in Firefox.  For some reason they always open in Konqueror (using Kubuntu, here) even though I've set Firefox as my default browser in KDE settings.  Anybody know how to fix this?  It's driving me nuts.  Thanks!

---

### Post by davidjmayo on 2007-07-17
Out of curiosity I tried your problem. I'm a kubuntu user with firefox and thunderbird as defaults and I had no problem.
 -The only difference I could think of was did you have firefox open already (I did - and links open in a new FF tab.)

---

### Post by gunksta on 2007-07-17
You can tell KDE what you want to use for your email client and web-browser.

Kmenu -> System Settings -> Default Applications (Top Row)

Then, just change the defaults to Firefox and Thunderbird respectively.

--andy

---

### Post by jespdj on 2007-07-17
I have the same problem (Kubuntu 7.04, 64-bit, Thunderbird, Firefox).

I have set my default web browser and e-mail program in KDE to Firefox and Thunderbird, but Thunderbird still insists on opening links with Konqueror instead of Firefox. Very annoying.

Is this a bug in Thunderbird? Thunderbird does not seem to have an option anywhere to choose how to open links in e-mails.

Any other ideas? :confused:

---

### Post by davidjmayo on 2007-07-17
> **jespdj said:**
> I have the same problem (Kubuntu 7.04, 64-bit, Thunderbird, Firefox).

I have set my default web browser and e-mail program in KDE to Firefox and Thunderbird, but Thunderbird still insists on opening links with Konqueror instead of Firefox. Very annoying.

Is this a bug in Thunderbird? Thunderbird does not seem to have an option anywhere to choose how to open links in e-mails.

Any other ideas? :confused:

You got me there. I just tried without firefox open just for the shear hell of it and  links in thunderbird still open in firefox.

I know you said you have them as defaults. Double check Kmenu==>System settings==>Default applications

Note: I use 32 not 64 bit but should it make a difference??

---

### Post by mike102282 on 2007-07-17
> **davidjmayo said:**
> You got me there. I just tried without firefox open just for the shear hell of it and  links in thunderbird still open in firefox.

I know you said you have them as defaults. Double check Kmenu==>System settings==>Default applications

Note: I use 32 not 64 bit but should it make a difference??

That shouldn't make a difference.

---

### Post by Rui Pais on 2007-07-17
hi,

you can try on thunderdird:
Edit->Preferences
then go:
Advanced->General

Click on 'Config Editor' and on editor check for a key:
**network.protocol-handler.app.http**
(you can make it if it doesn't exist) double click on it and set it to full path of the browser you want to use 
(in my case, as an example, i use swiftweasel, so it have: /usr/local/swiftweasel32/swiftweasel)

hth

---

### Post by jespdj on 2007-07-17
Rui Pais,

Thanks, that worked! =D>

---

### Post by Rui Pais on 2007-07-17
:)
glad it worked

---

### Post by anachreon_ on 2007-07-17
Thanks Rui Pais, that did the trick!  I am so happy now.  Love!

---

### Post by nolan- on 2007-07-18
Excellent, thats been bugging me, thanks!    :popcorn:

---

### Post by sqlpython on 2007-09-12
For those interested I posted the complete circle...
Thunderbird opening Firefox & Firefox opening Thunderbird to send an email

[http://ubuntuforums.org/showthread.php?p=3356507#post3356507](http://ubuntuforums.org/showthread.php?p=3356507#post3356507)

BTW Nolan Great MINI is it an S

---

### Post by jdier on 2007-09-21
I ran this:

```
$ sudo update-alternatives --config x-www-browser
```

---

### Post by c0oL-SG on 2007-11-06
> **jdier said:**
> I ran this:

```
$ sudo update-alternatives --config x-www-browser
```

Works great! Thanks man! :wink::wink:

---

### Post by ppedrok on 2007-11-06
Thanks, sqlpython! With a little correction (see your thread), it worked for me.
Question for developers: Why did it not work automatically anymore, like in Feisty?

---

### Post by Detonate on 2007-11-06
Also add the following line to the TB preferences:
[B]
network.protocol-handler.app.https[/B]

---

### Post by Fungyo on 2008-04-17
Thanks Rui Pais
Had to add new string. 
Preference name:
 ```
network.protocol-handler.app.http
```
Value:
```
/usr/bin/firefox
```
works for me

---

### Post by Rui Pais on 2008-04-17
> **Fungyo said:**
> Thanks Rui Pais
Had to add new string. 
Preference name:
 ```
network.protocol-handler.app.http
```
Value:
```
/usr/bin/firefox
```
works for me

Glad it worked :)

Dont' forget to check this sqlpython thread:
[http://ubuntuforums.org/showthread.php?p=3356507#post3356507](http://ubuntuforums.org/showthread.php?p=3356507#post3356507)
for make Firefox use Thunderbird (if it uses other mail client by default).

Have Fun

---

### Post by pbhj on 2008-05-01
Adding the about:config variable "network.protocol-handler.app.http" with value "/usr/bin/firefox" worked for me (ditto for https), Ubuntu 8.04, FF 3beta5.

The "alternates" config (which I tried first) didn't help at all.

---

