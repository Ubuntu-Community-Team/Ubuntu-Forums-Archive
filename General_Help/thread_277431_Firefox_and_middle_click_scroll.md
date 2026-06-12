---
title: "Firefox and middle click scroll"
date: 2006-10-14
forum: General Help
---

### Post by hafter on 2006-10-14
First of all , hello ubuntu users and excuse my english...:rolleyes: 

I've been a passive reader of this great forum since the release of the hoary edgehog and I have never been post anything ....

I really have a problem with firefox and middle click scroll , i'm attaching a little shot of my problem....

The problem is that when I scroll a webpage in firefox with my middle click button mouse , it leaves a trail of the cursor ](*,) and the trail don't dissapear, that means that if I scroll once or twice , i have one or two mouse trails along the web.

Any ideas of why ?? It really make the webs unreadable with all this trails ....

So , if anyone has an idea of why this happens , please , tell me how to fix it ... !

My specs
Ubuntu edgy
Aixgl
Nvidia 9625
gnome 2.16
amd 2.4ghz
512 ram
gforce 5200


Really pleased to meet you guys.:D 
Ubuntu Rocks.

[IMG]http://www.masquediseno.com/temporales/Pantallazo.jpg[/IMG]

---

### Post by aysiu on 2006-10-14
Don't know if there's an easy answer... not from me anyway.

But I do have some follow-up questions that may help you find the answer:

1. Has this always happened or did something recently change this behavior?

2. I noticed you have an NVidia graphics card. Do you have Nvidia drivers installed for those?

3. If you create a separate test user, does that test user experience the same problem in Firefox?

4. Does a similar problem appear in any other applications?

---

### Post by hafter on 2006-10-14
> **aysiu said:**
> Don't know if there's an easy answer... not from me anyway.

But I do have some follow-up questions that may help you find the answer:

1. Has this always happened or did something recently change this behavior?

2. I noticed you have an NVidia graphics card. Do you have Nvidia drivers installed for those?

3. If you create a separate test user, does that test user experience the same problem in Firefox?

4. Does a similar problem appear in any other applications?


Ok , gonna answer this ...
1- This always happened randomly , I use to re-install ubuntu once a month aprox. because of doing the things bad, and this error appears on one install , and on the next install it dissapear, or I update some packages and chachan .. the error returns.

2- I have installed the official beta drivers 9625 , but it happened always , with the 8xxx drivers and with the nvidia-glx package from ubuntu.

3- This problem appear in my user and in root user. Let's say it always happens don't matter what user I take.

4- [-(  Nope, this problem only appear in Firefox , Swiftfox.


;)  Well , it appears that it gonna be a difficult problem !..

---

### Post by aysiu on 2006-10-14
Yeah, it appears to be a problem.

What's AIXGL? Is that something like Beryl or Compiz? Maybe that's what's screwing things up?

---

### Post by hafter on 2006-10-14
> **aysiu said:**
> Yeah, it appears to be a problem.

What's AIXGL? Is that something like Beryl or Compiz? Maybe that's what's screwing things up?

Sorry ... isn't AIXGL .... is AIGLX :oops: :oops:

It happens with XGL with compiz and with AIXGL with beryl

I try killall beryl and the problem gone ...
Maybe a beryl/compiz bug ? an xserver bug ? firefox bug ?

I think I must learn to live with this bug... ](*,) 

Thaaanks for your response !

---

### Post by aysiu on 2006-10-14
It appears to be a Beryl/Compiz bug.
[https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/58622](https://launchpad.net/distros/ubuntu/+source/xorg-server/+bug/58622)

---

### Post by easterlingman on 2007-02-03
this is annoying.. doesn't look like it's ever getting fixed either.  one strange thing i've noticed is if i start autoscrolling half way into the scroll bar (like if the autoscroll image is partially obscured by it) then i never get trails.. this might be a temporary solution for some

---

### Post by gottferdamnt on 2007-02-03
any news about this bug?

[EDIT] Solved, Thank to the All-In-One Gesture add-on for firefox.

---

### Post by odzx on 2007-02-16
did not solve it for me.
installed all in one gestures but the trail remaines. for some reason this trail does not show up on every page just on most of them.

---

### Post by Godzig on 2007-02-21
I also have the same problem in firefox and also have the same thing happen if I use the middle mouse to scroll inside of a thunderbird email message.  If i really scroll madly up and down in firefox I can usually get it to hang my entire system forcing me to hard reboot.  Haven't figured out the why some pages and not others thing though.

and for what it's worth: edgy, nvidia, beryl. Only happens in beryl - and incidentally, the only glitch I've come across using beryl.

(all-in-one fix didn't work for me.)

---

### Post by t3soro on 2007-04-01
edit -> preferences
go to the advanced tab, and check "use autoscrolling"

---

### Post by authortitle on 2007-04-21
Annoying bug indeed, but I appear to have found a solution. Don't stop reading just because you've already tried the All in One Gesture extension...

1) Install the All in One Gesture extension for Firefox from [https://addons.mozilla.org/en-US/firefox/addon/12](https://addons.mozilla.org/en-US/firefox/addon/12)

2) Disable autoscrolling in Firefox (Edit > Preferences > Advanced, untick "Use Autoscrolling")

3) Go to the Preferences for All in One Gestures (Tools > Add-ons, select the extension and click Preferences)

4) (Optionally) untick all the "Enable" boxes except middle click scrolling (you can of course keep these on if you use them)

5) Go to the "Advanced Prefs 2" tab in the extension preferences, and tick "Autoscroll: show dedicated mouse cursor".

Seems to work for me, let me know your experiences. Very glad to have this sorted, I can't live without autoscroll and can't live with funny trails everywhere either ;)

---

### Post by odzx on 2007-04-21
> **authortitle said:**
> Annoying bug indeed, but I appear to have found a solution. Don't stop reading just because you've already tried the All in One Gesture extension...

1) Install the All in One Gesture extension for Firefox from [https://addons.mozilla.org/en-US/firefox/addon/12](https://addons.mozilla.org/en-US/firefox/addon/12)

2) Disable autoscrolling in Firefox (Edit > Preferences > Advanced, untick "Use Autoscrolling")

3) Go to the Preferences for All in One Gestures (Tools > Add-ons, select the extension and click Preferences)

4) (Optionally) untick all the "Enable" boxes except middle click scrolling (you can of course keep these on if you use them)

5) Go to the "Advanced Prefs 2" tab in the extension preferences, and tick "Autoscroll: show dedicated mouse cursor".

Seems to work for me, let me know your experiences. Very glad to have this sorted, I can't live without autoscroll and can't live with funny trails everywhere either ;)
works here to. thanks :guitar:

---

### Post by Gigzaholic on 2007-06-19
Thanks, worked for me too. Is there anyway to speed up the scrolling though?

---

### Post by Solrac924 on 2008-05-01
i enabled both "Use autoscrolling" **and** "Use smooth scrolling". it  slows it down a bit (due to the extra processes). :guitar:

---

