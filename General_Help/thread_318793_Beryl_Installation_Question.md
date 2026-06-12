---
title: "Beryl Installation Question"
date: 2006-12-14
forum: General Help
---

### Post by raveneffct on 2006-12-14
Ok so I added the repositories to Synaptic and installed Beryl....I see the Beryl Options in System>Preferences...but none of them seem to be doing anything? Can anyone help with this problem, thanks.

---

### Post by useResa on 2006-12-14
> **raveneffct said:**
> Ok so I added the repositories to Synaptic and installed Beryl....I see the Beryl Options in System>Preferences...but none of them seem to be doing anything? Can anyone help with this problem, thanks.
Maybe too obvious, but nevertheless let me ask the question:
Do you have Beryl running?

I - but this my preference - start Beryl by pressing <alt>-<F2> (will give you the Run application window) and entering *beryl-manager*.

---

### Post by raveneffct on 2006-12-14
> **useResa said:**
> Maybe too obvious, but nevertheless let me ask the question:
Do you have Beryl running?

I - but this my preference - start Beryl by pressing <alt>-<F2> (will give you the Run application window) and entering *beryl-manager*.

Yes it running, I see the diamond in my tray..but non of the animations selected are working :(

And I have 3d acceleration and all that good stuff.

---

### Post by d3v1ant_0n3 on 2006-12-14
If you run ```
beryl-manager
``` from terminal to start up beryl, what output do you get?

Also, what version of ubuntu are you using, and what graphics? (intel/nvidia/ati?)

---

### Post by raveneffct on 2006-12-14
> **d3v1ant_0n3 said:**
> If you run ```
beryl-manager
``` from terminal to start up beryl, what output do you get?

Also, what version of ubuntu are you using, and what graphics? (intel/nvidia/ati?)
```

 XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```

Using ATI, Current version of Ubuntu

---

### Post by d3v1ant_0n3 on 2006-12-14
Hmm...by all accounts, Beryl is much easier to set up on Ati cards using XGL, rather than AIGLX (which edgy has built in).

There's a howto [ HERE](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL) which may be of some use.

*EDIT* There's some more info on using 'ati' drivers rather than the 'flgrx' drivers- allows you to use AIGLX with ati cards  [ here](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/GCDrivers)

---

### Post by raveneffct on 2006-12-30
I am bumping this because, several weeks later, and trying to reinstall this multiple times I still get the same problems. Can someone please help. I have an ATI graphics card using fglrx and whenever I restart using the Beryl session, I never see the Beryl wobbly logo, all I see is the diamond in the corner and non of the effects are working. Thanks.

---

### Post by d3v1ant_0n3 on 2006-12-30
Did you follow the howto I posted?

---

### Post by raveneffct on 2006-12-30
Yes I did, which I just tried again not 5 minutes ago. I don't know what the problem is ](*,)

---

### Post by raveneffct on 2006-12-30
When I reload my repositories I do get some errors

[IMG]http://ourworld.cs.com/raveneffct/error.png[/IMG]

Does anyone know what these mean?

---

### Post by raveneffct on 2006-12-30
Well I finally got it to work...But, when I boot using Beryl session the theme on the task bar and windows is like a weird grey old looking style, and when i try to change emerald theme nothing happens..so, how do you change the theme?

And also if anyone knows anything about those errors, thanks guys and sorry for the double post.

---

### Post by kdub432 on 2006-12-31
I also have an ATI card, and use an xgl desktop to get beryl running. Aiglx gives me that same error message...

---

