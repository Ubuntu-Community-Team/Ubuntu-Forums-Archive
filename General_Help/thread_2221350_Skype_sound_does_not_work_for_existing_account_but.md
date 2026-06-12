---
title: "Skype sound does not work for existing account but new or guest session"
date: 2014-05-01
forum: General Help
---

### Post by mail-03146f06 on 2014-05-01
Hi, 

I have a very odd behavior for my Skype after upgrading from 12.10 to 14.04 over 13.10. Skype (Sound output) does not work for me as the old user aka the account I am using forever now. If I run a guest session or create a new user, it works like a charm.  So the hardware and sound is fine.

Sound plays for my user fine in all other applications but Skype (but it did fine with 12.10 previously).

So I suspect a problem with some configuration stored in my home. I removed the .Skype, I tried .config, all .gnome stuff, .gconf and the like. .bashrc as well. I do not have any idea where Skype or the Shell (Gnome classic here) might find something to shut the sound for Skype down.

Tried Gnome Fallback and Gnome Shell, as well as Unity. The same.

Does anyone have a clue where a certain setting or some auto-loaded-stuff might live that leaves my Skype for an old existing user desperate but causes not issue with new users or guest sessions?

Not to forget, I purged pulseaudio as well as Skype and reinstalled.

Thanks,
Rene

---

### Post by mail-03146f06 on 2014-05-02
It does seem to be something different. Today when playing with a new empty home and copying settings over piece by piece, it did not work at all for none of the mentioned scenarios. I brought back my regular setup and it did not work. I switched a little back and force between users and suddenly it works. Simply restarting Skype does not help, there is something to it...

---

### Post by Habitual on 2014-05-02
in terminal of the affected user > 
```
mv ~/.Skype ~./Skype.backup
rm ~/.Skype
```
Start Skype and login as your usual ID and exit immediately, shutting down Skype.
back in Terminal for the affected user >
```
cd ~./Skype.backup
find -name  main.db -exec cp {} ~/.Skype \ ;
```
Start Skype, test.

The main.db copy will preserve chat histories.
Your contact list will be repopulated from the Skype "mothership" where they are stored.

Hope that helps.

---

### Post by mail-03146f06 on 2014-05-04
Thanks for the hint, but as mentioned before, I tried that with a blank dir and it did not work.

I found out that the working Skype for Guest and a new user was misleading. Yes, it works, but it also fails. Also found Skype working with my account after a minute or two of strange noise (after the first sound it tried to make) and once it made another sound, it worked fine.

Currently trying this and will observe over time if this helps: "The newer implementation of the PulseAudio sound server uses timer-based  audio scheduling instead of the traditional, interrupt-driven approach...."   [https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling](https://wiki.archlinux.org/index.php/PulseAudio#Glitches.2C_skips_or_crackling)

Works right now for me and the home dir assumption was totally wrong.

---

### Post by mail-03146f06 on 2014-05-15
This solved it. No problem.

---

