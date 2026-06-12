---
title: "Display scrambled after changing any resolution in Display Setting"
date: 2020-12-04
forum: General Help
---

### Post by tclam662 on 2020-12-04
Hello, I am quite new to Ubuntu and Linux and I have got a little problem recently when installing my Ubuntu 20.04.1 LTS desktop on a Dell R340(using onboard VGA port). My display will scramble if I change to resolutions other then what was auto detected by system in Display setting (Right-click on the desktop-> Display Setting):
[[IMG]https://i.ibb.co/YZbRNxs/Clipboard02.png[/IMG]]("https://i.ibb.co/YZbRNxs/Clipboard02.png")

i.e. when I plug in a Monitor, the system automatically set it to 1920 × 1080 but if I change it to anything other then 1920 × 1080 and click apply, the display scrambles right away and I have to Esc to revert the resolution. However I am sure that my current screen supports other resolutions as I have been using it in Windows 10. The same scrambled display also happens after logout and the User login screen cant be displayed properly so I have to guess, once logged in successfully the display resumes normal.

I have also tried replacing other monitors (with other automatically detected resolution) but I have got the same problem. Now a Spider Duo IP-KVM (which emulate itself as an VGA monitor supporting max 1600x1200, ubuntu auto set resolution to  1600x1200 when I plug it in) is now attached to the R340 and again the display scrambles when I try to change the resolution to anything other then  1600x1200.

Any ideas?

[[IMG]https://i.ibb.co/DMC7vr8/sss.png[/IMG]]("https://i.ibb.co/DMC7vr8/sss.png")
[[IMG]https://i.ibb.co/7nFhRxR/sss.png[/IMG]]("https://i.ibb.co/7nFhRxR/sss.png")
[[IMG]https://i.ibb.co/nkvkZTC/sss.png[/IMG]]("https://i.ibb.co/nkvkZTC/sss.png")
Sorry that I cant copy from the KVM.

---

### Post by CelticWarrior on 2020-12-04
Welcome.

Your iGPU is very very old and the driver running it (and the only one you can use) is a "best effort" kind of situation.
I suggest you use the native resolution only.

---

### Post by tclam662 on 2020-12-05
Thanks for the advice, I will stick to the default res for now

---

