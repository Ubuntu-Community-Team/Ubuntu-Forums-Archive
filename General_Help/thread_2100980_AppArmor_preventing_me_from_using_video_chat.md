---
title: "AppArmor preventing me from using video chat"
date: 2013-01-03
forum: General Help
---

### Post by Mozai on 2013-01-03
I used to be able to use Google's talk/hangout services to video chat with my mother.  Today, I couldn't.  I checked /var/log/syslog to see if the USB camera was detected.  This is what I saw:

[FONT="Courier New"]Jan  3 09:26:23 deunan kernel: [251086.531560] type=1400 audit(1357223183.407:265): apparmor="DENIED" operation="open" parent=1 profile="/usr/lib/firefox/firefox{,*[^s][^h]}" name="/dev/video0" pid=16606 comm="GoogleTalkPlugi" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0[/FONT]

When did firefox's apparmor change to prevent it from being allowed to access /dev/video0 ?  And what's the proper way to tell apparmor to permit firefox read-access to my video camera?

For now I just shut down apparmor completely -- my mother was waiting for me -- and I'll reactivate it when we finish.  I really wish not to deactivate apparmor completely every time I wish to video-chat with family.

---

### Post by Mozai on 2013-01-03
Other stuff that apparmor prevents firefox from accessing:

[FONT="Courier New"]# sudo grep 'apparmor="DENIED"' /var/log/syslog |awk '{print $13" "$16;}' |sort -u[/FONT]

requested_mask="c" name="/run/shm/google-nacl-shm--16606.1"
requested_mask="c" name="/run/shm/google-nacl-shm--16606.2"
requested_mask="c" name="/run/shm/google-nacl-shm--16606.3"
requested_mask="c" name="/run/shm/google-nacl-shm--16606.4"
requested_mask="c" name="/run/shm/google-nacl-shm--16606.5"
requested_mask="c" name="/run/shm/google-nacl-shm--16606.6"
requested_mask="r" name="/dev/video0"
requested_mask="r" name="/etc/apt/sources.list"
requested_mask="r" name="/etc/udev/udev.conf"
requested_mask="rw" name="/dev/nvidiactl"
requested_mask="x" name="/usr/bin/lsb_release"

---

### Post by conradin on 2013-01-03
AppArmor isnt something I run, but I would geuss that there must be a config file, permision setting, or profile that controls what is or isnt allowed to run. The wiki looks like a good place to start.
[http://wiki.apparmor.net/index.php/Documentation](http://wiki.apparmor.net/index.php/Documentation)

---

### Post by vasa1 on 2013-01-03
I'm not expert in Apparmor but ...
Re-enable Apparmor.
Put Firefox in **complain** mode by running ```
sudo aa-complain /path/to/firefox
```
Do your video chat which should now work.
Run ```
sudo aa-logprof
```
You'll now get a bunch of prompts. How you respond will depend on the nature of each prompt.
The final prompt will be to save changes. Agree to save the changes to the profile.
Then do another video chat.
Again run sudo aa-logprof. Again answer all prompts and save. Depending on the situation, you may have to repeat the process. Sometimes, choosing the "glob" alternative may be appropriate.
Finally, when aa-logprof has nothing further to suggest, you could put Firefox back into **enforce** mode by running ```
sudo aa-enforce /path/to/firefox
```. Your videochat should then work even with the Firefox profile enforced.

BTW, it isn't necessary to turn off Apparmor altogether. Just put the suspect profile in **complain** mode to analyze the situation as I've tried to explain above.

---

