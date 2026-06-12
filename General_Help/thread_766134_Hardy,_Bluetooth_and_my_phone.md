---
title: "Hardy, Bluetooth and my phone"
date: 2008-04-25
forum: General Help
---

### Post by estanton on 2008-04-25
Just upgraded to Hardy this afternoon, seems fine, only problem is that I can't put anything to my phone. I can find it fine, even browse the phone and it's files using Bluetooth Applet but when I try and drag files across it says:

Error while copying "whatever"
There was an error copying the file into obex://MAC Address/.
and under details:
Operation not supported by backend

I'm assuing I'm just missing something, any ideas on what that is?

---

### Post by estanton on 2008-04-25
ah apparently it's simply not supported yet. Ouch. Has gnome-obex-send been discontinued, the launcher I used for this purpose has ceased to function. it just states:
```
There was an error launching the application.
Details: Failed to execute child process "gnome-obex-send" (No such file or directory)

```

---

### Post by monoufo on 2008-04-25
its been discontinued for several weeks. you have to use the new wah.

---

### Post by estanton on 2008-04-25
what is wah?

---

### Post by wild_oscar on 2008-04-25
I second that question: what is "wah"?

---

### Post by derailed1 on 2008-04-27
hardy is driving me nuts!  I have all the same bluetooth headset problems like everyone else.  Any help?

---

### Post by mad chey on 2008-04-30
> **monoufo said:**
> its been discontinued for several weeks. you have to use the new wah.

i agree with the others 

What is wah?

pls could your answers be more informative

---

### Post by steveneddy on 2008-04-30
> **estanton said:**
> what is wah?

Wireless Audio Headset firmware

---

### Post by amoore on 2008-04-30
I bluetooth head set problems too. I just can get the headset to pair!

---

### Post by mad chey on 2008-05-01
ok, another stupid question then

where do i get this wah from

synaptic not listing "Wireless Audio Headset Firmware"

and google, well lets say my answer to that was "no i dont want to xxxxx buy a headset"


if you dont mind pls a linky, or im gonna have to go back to gutsy,

---

### Post by steveneddy on 2008-05-01
I'm tired of the Bluetooth issues - I'm going back to Gutsy until they get more bugs worked out.

---

### Post by steveneddy on 2008-05-01
> **steveneddy said:**
> I'm tired of the Bluetooth issues - I'm going back to Gutsy until they get more bugs worked out.

That's funny, it works great now.

huh.

---

### Post by derailed1 on 2008-05-02
What did you do to get it working?  Hardy looks awesome but I wont upgrade until the bluetooth is resolved for me :(

---

### Post by mad chey on 2008-05-03
please yes, let us know how you fixed it

---

### Post by steveneddy on 2008-05-03
> **derailed1 said:**
> What did you do to get it working?  Hardy looks awesome but I wont upgrade until the bluetooth is resolved for me :(

I don't really know. I made sure that bluez-gnome was the hardy version, I reinstalled all of the bluetooth stuff and all the bluez stuff.

I restarted a couple of times. 

I made sure the switch was turned on.

I don't know what exactly I did, but I suddenly discovered that one day after this post that is worked, perfectly, and I am happy.

I didn't tweak any config files at all.

I uninstalled blueman and just use the stock bluetooth software and it works great. Blueman was good for Gutsy, but not Hardy it seems, although it is now in the repos.

Now that I think about it, the same thing happened in Gutsy for me. Nothing then everything perfect. I don't understand, but it works and I am happy.

Did you see the round Compiz?

---

### Post by tanas on 2008-05-09
It did it!
(So my problem was that AFTER the upgrade to Hardy, I could no longer send files from the phone to the computer.. but the other way around was ok)-

I downgraded the bluez-utils in synaptic to the gutsy version (3.19, just add 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main
to the repositories list) and now my computer is again able to receive files from the mobile phone.

---

### Post by estanton on 2008-05-20
> **steveneddy said:**
> Wireless Audio Headset firmware

I fail to understand how the Wireless Audio Heaset firmware will help me to send files to my phone. In any case I figured it out, select the files you want right-click and select send.

---

