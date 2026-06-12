---
title: "Update results in sun-java5-plugin error"
date: 2006-12-08
forum: General Help
---

### Post by jazzguitar247 on 2006-12-08
the orange update icon has been showing on my panel (i have edgy) and when i click it nothing happens :confused: - which is fine for now...i can update by right clicking (or so i thought). So i select show all updates, enter my password, - the screen flashes and returns to whatever i was doing before as if nothing happened. So then i click install all updates and it is off and running....kind of

after it installs some of the updated packages it gives me this error
[FONT="Courier New"]
E: sun-java5-plugin: subprocess post-installation script returned error exit status 2[/FONT]

i would copy the package terminal output here but i don't know how
So then i go to the terminal window and do the following

[FONT="Courier New"]sudo dpkg --configure -a
Setting up sun-java5-plugin (1.5.0-10-0ubuntu1) ...
update-alternatives: unable to make /usr/lib/iceweasel/plugins/libjavaplugin.so.dpkg-tmp a symlink to /etc/alternatives/iceweasel-javaplugin.so: No such file or directory
dpkg: error processing sun-java5-plugin (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 sun-java5-plugin[/FONT]
 ](*,) ](*,) ](*,) ](*,) 
I get that error every time.
Where can i find what the statuses are?
where can i find what subprocess script they are talking about?
I want to learn so please help me fix this!

cheers!
russaad

---

