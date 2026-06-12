---
title: "Upgrade to 16.04 LTS give a  regresson in behavior"
date: 2016-08-07
forum: General Help
---

### Post by georgesgiralt on 2016-08-07
Hello !
I own a Lenovo laptop with a couple of power indicator LED. On 14.04 LTS I fixed a wrong behaviour (the led flashes after waking up from sleep mode) by providing a script in /etc/pm/sleep.d/ to send the correct value in /proc/acpi/ibm/led.
This has worked for years but since the upgrade, the script is still here but the behaviour is, as it was, erratic. The script in sleep.d is not run any more. 
What's wrong ? How should I fix it ?

---

### Post by pqwoerituytrueiwoq on 2016-08-07
16.04 uses systemd 
this will help you
[http://askubuntu.com/questions/609695/does-systemd-read-etc-pm](http://askubuntu.com/questions/609695/does-systemd-read-etc-pm)

---

### Post by georgesgiralt on 2016-08-07
Thank you for your answer.
start of rant. 
I'm astonished (polite and politically correct status...) to see that a distro which is for "human beings" with the user in mind change things that did not need fixing and wreck havoc a system. It would have been fancy to provide a migration script from /etc/pm.d to the systemd script location in the distro upgrade package.. 
I still do not understand the desire to "fix" things that are not broken and run fine. And had run fine for years, are perfectly documented, well understood and dependable... Which, if I'm not mistaken systemd is not. 
End of rant.

---

### Post by pqwoerituytrueiwoq on 2016-08-07
all the main distros are now using systemd
that is one of the reason i am still procrastination on my upgrade on my desktop
just have not felt like finding all the little stuff i will need to fix

---

