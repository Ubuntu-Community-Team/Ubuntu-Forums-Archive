---
title: "Thunderbird not starting"
date: 2007-02-26
forum: General Help
---

### Post by madsurfer on 2007-02-26
Hi

I have just installed thunderbird using the following instuctions:

[http://tuxicity.wordpress.com/2007/01/24/install-native-mozilla-thunderbird-20-beta-2-on-ubuntu/](http://tuxicity.wordpress.com/2007/01/24/install-native-mozilla-thunderbird-20-beta-2-on-ubuntu/)
When I try to start thunderbird I get the following error:-
 Could not launch application

Failed to execute child process"thunderbird" (permission denied)

If I check all the permissions they seem to be ok. When I start it from the cmd line it seems to be working ok. Does anyone know what is going on?

Adrian

---

### Post by Maestro23 on 2007-02-26
Open a terminal and type:

> whereis mozilla-thunderbird

Should give you the path to the .bin

Try to launch from terminal and post back what happens. Ex on mine:

> mozilla-thunderbird

---

### Post by madsurfer on 2007-02-26
Well I have done this and got the following:

 whereis mozilla-thunderbird
mozilla-thunderbird:

have also done 
  adrianr@geko80:~$ which thunderbird
adrianr@geko80:~$ which mozilla-thunderbird

this kind of indicates its not on the $PATH


found it, the PATH was wrong. will try it again after a reboot just to be sure

Thanks

Adrian

---

