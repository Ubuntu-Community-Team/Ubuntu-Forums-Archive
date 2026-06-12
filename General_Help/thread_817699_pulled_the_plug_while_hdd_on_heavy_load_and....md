---
title: "pulled the plug while hdd on heavy load and..."
date: 2008-06-03
forum: General Help
---

### Post by eldragon on 2008-06-03
yes......knacked the notebook :D
wouldnt boot. i popped in a knoppix cd in, and did a fsck to the / partition
found lots of errors, inconsistencies and what not.

now i was able to boot, but not everything was as i had left it.

most things got fixed by a simple apt-get install --reinstal package_in_trouble

this fixed
-thunderbird
-gnome-do
-wireless

so far so goo.

but...my firefox profile died :(, had to delete it completely. not that much of a deal.

so. what went wrong? why oh why a fsck didnt fix this like it should have. it kind of went way back in time or something.

i had to reconfigure /etc/network/interfaces for example.

gonna keep looking for problems :D
so...anyone got a better idea on how to recover better from a mistake like this?

---

### Post by VMC on 2008-06-03
Depends on what the system was doing at the exact time you turned the power off. By the way, you said this happened on your laptop. That means you would have had to pull the battery out as well, correct?

This sort of thing has happened to me in the past without much damaged. 

Do you know why the system was doing the hard drive activity? Maybe you could have open a terminal even using Alt+Ctrl+F1 and executed a shutdown. I use Acronis and always keep a backup. At least to the point that I can recover to some reasonable configuration.

---

### Post by eldragon on 2008-06-04
i had virtualbox open (didnt break at all)

i had matlab open (sitting idle, didnt break either)

i had inkscape open (i think this is the reason for hdd usage)

essentially, the computer was next to useless due to the activity. hitting ctrl-alt-f1 took 5 minutes to respond, loging in another 3 minutes. it never actually gave me the prompt....

the hdd had just done its usual 38boot fsck during that boot.

ive reinstalled the entire mono suit and still i cant get mono based apps to work, they all segfault :(, reinstalling those isnt helping either. i dont want to download all installed packages again, so, does anyone got an idea on what to do next (dont want to format, need the system operational. or partial opeartional as it is now)...

f-spot and gnome-do do not work. exit with the same error.

---

