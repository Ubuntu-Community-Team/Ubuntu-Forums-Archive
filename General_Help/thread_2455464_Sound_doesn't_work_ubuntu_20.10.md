---
title: "Sound doesn't work ubuntu 20.10"
date: 2020-12-20
forum: General Help
---

### Post by revale on 2020-12-20
Hello everyone,

I installed ubuntu 20.04 on my Lenovo X1 Tablet.

First I had sound but then it stopped working. I've read a lot in google about it and tried various settings but it never worked. 

I have uninstalled and reinstalled pulse audio as well as alsa-mixer. No change though.

Then I upgraded to Ubuntu 20.10 but still same problem.

Unfortunately (coming from Windows 10) I'm not familiar with the terminal. 

Could somebody tell me a way how to identify the issue?

Thank you

Btw... the sound is working fine under Windows.

---

### Post by CelticWarrior on 2020-12-20
Welcome.

> [COLOR=#000000]Unfortunately (coming from Windows 10) I'm not familiar with the terminal.[/COLOR]

Why not? Terminal in Windows (cmd) and especially Powershell is the most powerful tool for Windows administration. What you're saying in this sentence is that you never cared to be anything more than just a regular user. The good news is you can be the exact same "regular user" with any mainstream Linux distro if you want. The reason why we so often lead users to / give support with the terminal is because there are more than a dozen of different desktop environment and variants in the Ubuntu family alone and each one potentially has different settings/approaches, but the core OS is the same therefore the same command just works independently of your specific "flavor" and customization.

Regarding your issue the first thing I would ask is about Windows' Fast Startup. If enabled it can cause all sort of issues including hardware unavailability when dual- or multi-booting. As such, please disable it and shutdown Windows before booting Ubuntu. Any change?

---

### Post by revale on 2020-12-20
Thanks for the help.

I have disabled fast startup in Windows now. But no change.

What I mean by "I'm not familiar with the terminal" is that I still rely mostly on copy and paste commands in Ubuntu.

---

### Post by ActionParsnip on 2020-12-21
Please follow
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Give the output of Step 3

Thanks

---

