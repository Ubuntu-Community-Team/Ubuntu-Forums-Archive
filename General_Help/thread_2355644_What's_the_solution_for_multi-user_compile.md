---
title: "What's the solution for multi-user compile?"
date: 2017-03-15
forum: General Help
---

### Post by 3shoryuken on 2017-03-15
Hi there,
    I have some experience on ubuntu; but I want to share my status and see if there would be solutions:

     I have an PC with I7 and 16GB RAM for compiling android source code with Ubuntu 16.04 ; and now I need to share it with others;

     I wondered if I could use remote desktop to connect to my server and I could have have an UI and enjoy the faster CPU of there server instead of keeps sitting in front of it -- and there would be conflicts if both of us want to use that.

      Why UI is nessary? Because some of my test tools is UI based and it needs to connect to X server :(

      Is there any solutions for such situation ? BTW, we do document and mail job on WINDOWS... so I wondered if there is windows Remote Desktop Tools.

      And I tried install xfce before -- the problem is it is not ubuntu native and I never remove them from system successfully :(.

      Any ideas?

---

### Post by TheFu on 2017-03-15
Use X/Windows if on the same LAN.  This is extremely common. $ ssh -X /full/path/to/program

Use x2go (or any NX) if NOT on the same LAN.

Since the early 1980s, Unix with X/Windows has supported running GUI applications over the network.

Use the normal methods of group management to allow different userids to access/write to the same storage areas, if you need that. This is extremely common.

---

### Post by 3shoryuken on 2017-03-15
Thanks; I will take a try.

---

