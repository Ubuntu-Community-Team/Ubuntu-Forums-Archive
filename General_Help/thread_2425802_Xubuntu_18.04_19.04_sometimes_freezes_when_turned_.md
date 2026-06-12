---
title: "Xubuntu 18.04 19.04 sometimes freezes when turned on on logo"
date: 2019-08-30
forum: General Help
---

### Post by stafik1993 on 2019-08-30
Sometimes when I turn off the computer, it hangs on the logo. What is the problem? Prior to this, the computer did not want to boot with the 4.15 kernel. When I updated the BIOS, the computer started to boot. Maybe the problem is in the bios again?

Here is a hang [[FONT=Verdana]https://ibb.co/PcYvDLq [/FONT]]("https://ibb.co/PcYvDLq")

[COLOR=#222222][FONT=Verdana]Mysystem unit -[/FONT][/COLOR] HP-Compaq-dc5800-Microtower

---

### Post by Artim on 2019-08-31
Is this 18.04 or 19.04?  The title indicates *both*, which isn't possible unless you are dual-booting both versions of the same distro.  That would be very problematic!

---

### Post by stafik1993 on 2019-08-31
[QUOTE = Artim; 13883911] &#1069;&#1090;&#1086; 18.04 &#1080;&#1083;&#1080; 19.04? &#1053;&#1072;&#1079;&#1074;&#1072;&#1085;&#1080;&#1077; &#1091;&#1082;&#1072;&#1079;&#1099;&#1074;&#1072;&#1077;&#1090; &#1085;&#1072; *&#1086;&#1073;&#1072;* , &#1095;&#1090;&#1086; &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1077;&#1089;&#1083;&#1080; &#1074;&#1099; &#1085;&#1077; &#1079;&#1072;&#1075;&#1088;&#1091;&#1078;&#1072;&#1077;&#1090;&#1077; &#1086;&#1073;&#1077; &#1074;&#1077;&#1088;&#1089;&#1080;&#1080; &#1086;&#1076;&#1085;&#1086;&#1075;&#1086; &#1080; &#1090;&#1086;&#1075;&#1086; &#1078;&#1077; &#1076;&#1080;&#1089;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1080;&#1074;&#1072;. &#1069;&#1090;&#1086; &#1073;&#1099;&#1083;&#1086; &#1073;&#1099; &#1086;&#1095;&#1077;&#1085;&#1100; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084;&#1072;&#1090;&#1080;&#1095;&#1085;&#1086;! [/ QUOTE] 

On both versions, the computer freezes after shutting down. Now installed 18.04

---

### Post by Artim on 2019-08-31
And did that fix it?

---

### Post by stafik1993 on 2019-09-01
> **Artim said:**
> And did that fix it?
How to fix this bug?

---

### Post by guiverc on 2019-09-01
Does it work if you enter a command to shutdown?  ie.

`sudo shutdown -h now` 
`sudo init 0` etc

From what I can see the system did shutdown correctly; shutdown strictly refers to the OS has stopped running (it's not hanging, it's just stopped), your issue is the power didn't turn off after shutdown. The `-h` option in my first command tells `shutdown` to include a HALT of power after shutdown (but not all systems do HALT power; particularly mainframes or larger Z series systems; power-off is the default only for smaller systems).

---

### Post by stafik1993 on 2019-09-01
[QUOTE=guiverc;13884285]Does it work if you enter a command to shutdown?  ie.

`sudo shutdown -h now` 
`sudo init 0` etc

The fact is that you can only turn off the computer with power. sudo shutdown -h now cannot be written. The computer does not respond to the keyboard. Also on the system unit, the button is lit.

---

