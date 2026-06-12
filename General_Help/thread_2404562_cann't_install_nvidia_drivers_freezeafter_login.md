---
title: "cann't install nvidia drivers freezeafter login"
date: 2018-10-25
forum: General Help
---

### Post by nicestuff on 2018-10-25
so After installing ubuntu on my laptop, i cann't login (frreze after login)

it is probably a problem with my nvidia card (GTX 10502GB).

But (ctrl + alt + F7 doesn't work :(  (only a log screen or something)
and if i give a boot paramter ('nomodeset') it boot on a black screen (only white line)


can someone help me with this issue?

---

### Post by diegogermangonzalez on 2018-10-25
Which version of Ubuntu?
If it is 18.10 there is a reported problem.
Start the system in recovery mode (second line of the Grub) and choose the option Root console.
scribe
sudo apt remove --purge nvidia-*
and then sudo reboot

---

### Post by nicestuff on 2018-10-25
It works, but i exexted the commands after add the bootparam: [B]'acpi=off' 

Thanks!
[/B]

---

