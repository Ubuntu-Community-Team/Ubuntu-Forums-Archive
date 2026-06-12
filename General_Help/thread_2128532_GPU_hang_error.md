---
title: "GPU hang error"
date: 2013-03-23
forum: General Help
---

### Post by Hvidemose on 2013-03-23
Hey there awesome people!

 

 My 12.10 has started to report about an error, which It by the way doesn't give any info about. After the error it asks my this question:
 

 **Apport has detected a possible GPU hang.  Did your system recently lock up and/or require a hard reboot?**
 

 How can I find out what's wrong, so I can fix it?

---

### Post by father_ted on 2013-03-23
Yes. The latest updates have brought on this problem for me too - and its driving me nuts. There is a bug on launchpad for something like it. 

If anyone knows a fix please share.

---

### Post by Hvidemose on 2013-03-24
[SIZE=3]Yep, pretty annoying! Has any body else experienced this problem?

Solution? Anything?[/SIZE]

---

### Post by Jack Kelly on 2013-03-25
I'm getting this same error.

---

### Post by slokenafk on 2013-03-25
Im having the same error continuously.  Ive tried numerous things such as using unity or gnome.  Nothing works so far.  Best I have found is to just decline the option to report any errors and it wont bother me for a little while.  So far this has worked.  If I keep reporting the error eventually it eats up my cpu power and I have to reboot.


Considering I have reported this error hundreds of times, repeats wont exactly help.

Hope this helps otherts for now.:-?

---

### Post by TDully on 2013-03-26
I just want to let ya'll know, your are not alone !!! there are several threads out there on same issue! Depends on how it is stated on forum. However, from all i have seen it all has to deal with 
 { /usr/share/apport/apport0gpu-error-intl.py } i can also say, this issue IS know, yet no work around, { other than disabling Apport  } or an actual fix yet! Plus, from all the research i have done, this is know, from the time Intel HD graphics where beening deployed, and no actual "FIX" yet... 
Driving Me Nucking Futz toooo...

---

### Post by slokenafk on 2013-03-30
Any news of a possible fix?

EDIT:

Here is bug on launchpad

[https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1073626](https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1073626)

---

### Post by slokenafk on 2013-04-02
Patch was released!!!\\:D/

---

### Post by adyst on 2013-04-03
I just updated all to latest, xdiagnose included, I'm still getting the same error...

---

### Post by habana on 2013-04-03
> slokenafk
    **Re: GPU hang error**

    Patch was released!!! 

The reported bug was for a "false gpu hang". Most of the users currently reporting a gpu hung error are experiencing a real problem e.g. firefox freezing. There is no fix yet.

---

### Post by Bigneil on 2013-04-08
yup, pretty annoying.

---

### Post by Hvidemose on 2013-04-13
Ok, getting tired of this problem... Does any body know, if it helps to reinstall the system?

---

### Post by mörgæs on 2013-04-13
If you do reinstall, could you please try 13.04 beta and see if it is fixed there?

---

### Post by piedog98 on 2013-04-24
please i need fix. my computer freeze and i have to hard boot. very annoying when play counter strike

---

### Post by mörgæs on 2013-04-24
This posting style does not bring you closer to a fix. 
A thorough description of the bug including hardware and all the Buntu releases you have tried would be a good beginning.

---

### Post by rocketfish201 on 2013-04-24
I get the GPU hang error a lot if I have smooth scrolling enbaled in Firefox. Turning it off seems to fix it for me.

---

### Post by Hvidemose on 2013-04-26
Did not work to upgrade to 13.04. Will try to reinstall soon, then we will se...

---

### Post by habana on 2013-04-26
> mörgæs

    Re: GPU hang error
    If you do reinstall, could you please try 13.04 beta and see if it is fixed there? 

I upgraded to 13.04. All OK now.

---

### Post by Hvidemose on 2013-04-27
The upgrade didn't work for me, but reinstall did... So problem solved, although it wasn't really solved...

---

### Post by Macoy Villalobos on 2013-04-27
Same here. . and yes it is annoying. I hope someone could find a solution.. :?

---

