---
title: "Anti-spyware program?"
date: 2005-09-11
forum: General Help
---

### Post by Vinze on 2005-09-11
Can anybody tell me if I have a spyware risk on Linux, if not, why not, if yes, do you know a program against this? Thanks in advance.

---

### Post by krusbjorn on 2005-09-11
There is no risk of getting spyware in linux. 
Why not? There aren't any.

---

### Post by Vinze on 2005-09-11
[QUOTE=krusbjorn]There is no risk of getting spyware in linux. 
Why not? There aren't any.[/QUOTE]


How come? I mean, there also are viruses for Linux (though little), so why not spyware? Not that I'd want spyware or anything :D

---

### Post by krusbjorn on 2005-09-11
Most people run Windows as administrator (with root access), meaning code that is executed in explorer can mess around as much as it wants. In Linux, you dont have root access and Firefox is more secure than IE.

And, you know, if there were any spyware for Linux circulating, you would have to install it manually, without knowing it. People cant hide that type of stuff in their open source programs without slashdot screaming "SPYWARE! SPYWARE!" ;)

So basically, there is no spyware for linux, because people dont bother writing it, since it wouldnt work anyway.

---

### Post by Vinze on 2005-09-11
[QUOTE=krusbjorn]Most people run Windows as administrator (with root access), meaning code that is executed in explorer can mess around as much as it wants. In Linux, you dont have root access and Firefox is more secure than IE.

And, you know, if there were any spyware for Linux circulating, you would have to install it manually, without knowing it. People cant hide that type of stuff in their open source programs without slashdot screaming "SPYWARE! SPYWARE!" ;)

So basically, there is no spyware for linux, because people dont bother writing it, since it wouldnt work anyway.[/QUOTE]

Ah yes, that's true. Then another question, how come there are viruses for Linux while the above is true?

---

### Post by krusbjorn on 2005-09-11
Perhaps someone has written a few viruses for linux, but they dont work either.  There is no risk at all getting a virus, for the same reasons as i stated above.

---

### Post by Vinze on 2005-09-23
[QUOTE=krusbjorn]Perhaps someone has written a few viruses for linux, but they dont work either.  There is no risk at all getting a virus, for the same reasons as i stated above.[/QUOTE]
 What I understand now is that you can have viruses on Linux, but you need to consciously install them, having root privileges. That's why Linux is safe and Windows isn't :D

---

### Post by fordfan753 on 2005-09-23
If you're smart the worst Linux virus can only ever break your home directory, so most people don't bother making Linux viruses, they stick to an easier target....*cough*I'm not even gonna say thing one :P

At last count there was only around 100 viruses for Linux, that all basically did the same thing....for Windows there are many tens of thousands....which one seems most safe?

---

### Post by Vinze on 2005-09-23
[QUOTE=fordfan753]If you're smart the worst Linux virus can only ever break your home directory, so most people don't bother making Linux viruses, they stick to an easier target....*cough*I'm not even gonna say thing one :P

At last count there was only around 100 viruses for Linux, that all basically did the same thing....for Windows there are many tens of thousands....which one seems most safe?[/QUOTE]


Indeed, I think it's almost impossible to get a Linux virus, or you have to get it on purpose. If you would be so stupid to consciously install a virus, you wouldn't be able to, because you do not have root rights, and you don't know how to get them.

---

### Post by jimcooncat on 2005-09-23
Korean Mozilla Binaries Infected
[http://linux.slashdot.org/article.pl?sid=05/09/21/1252213&tid=154&tid=172&tid=106](http://linux.slashdot.org/article.pl?sid=05/09/21/1252213&tid=154&tid=172&tid=106)

Of course, you have to be sensible about where you get your software!

Personally, I stick with the official Ubuntu and Debian repositories, else I compile from source after some verification it's the real thing.

If it's your intention to load stuff from outside the distro, the forums here are a very good place to get advice and recommendations.

Antivirus and antispyware programs are, IMHO, a bad deal for consumers; the OS vendor should be held to the fire to fix the security of the system, not cover it up.

---

### Post by Ken.Lank on 2005-09-23
[QUOTE=Vinze]Indeed, I think it's almost impossible to get a Linux virus, or you have to get it on purpose. If you would be so stupid to consciously install a virus, you wouldn't be able to, because you do not have root rights, and you don't know how to get them.[/QUOTE]

If the virus is embedded in a software installation routine, then when the user was installing the software they would provide the 'root' privs because they are used to donig this.  So it's not that you would be consciously installing it.

---

### Post by fordfan753 on 2005-09-23
[QUOTE=Ken.Lank]If the virus is embedded in a software installation routine, then when the user was installing the software they would provide the 'root' privs because they are used to donig this.  So it's not that you would be consciously installing it.[/QUOTE]

I can see how this would happen...but how many people must actually check through the source to see if the package is doing it's best for their system. With everything open sourced it's hard to hide things, I know it only takes one line, but the hardest place to hide something is in plain sight. Using official mirrors would also be a security advantage.

---

### Post by Vinze on 2005-09-23
[QUOTE=Ken.Lank]If the virus is embedded in a software installation routine, then when the user was installing the software they would provide the 'root' privs because they are used to donig this.  So it's not that you would be consciously installing it.[/QUOTE]

Yes of course, but you do have to be consciously installing something. And if you're smart enough, you don't install anything from sources you don't trust. And I'm sure the Ubuntu and Debian reprositories widely satisfy your needs. And still, even if the virus was enclosed in a program, there's a small chance you get it because there are so little viruses :D . And still, it's a lot safer than Windows  ;)

---

### Post by jimcooncat on 2005-09-23
[QUOTE=Vinze]Yes of course, but you do have to be consciously installing something. And if you're smart enough, you don't install anything from sources you don't trust. And I'm sure the Ubuntu and Debian reprositories widely satisfy your needs. And still, even if the virus was enclosed in a program, there's a small chance you get it because there are so little viruses :D . And still, it's a lot safer than Windows  ;)[/QUOTE]

Gee, Vinze, you were doing great, but I don't know about the last sentence. Is a trojan infection during a Linux app install any safer than on Windows? 

Compare deleting everything on my C: drive (that has no network shares mounted under that hierarchy) and rm -rf / (that has all my network shares mounted under it). The power of a Linux root account is awsome to behold.

Unless apt is using some kind of sandbox approach during installations (and I don't know if it does or not), I'd say no, your local system is quite well hosed no matter which OS you're using. If the network may actually be safer with Windows with this actual example -- but trojan writers do know how to browse SMB shares quite well.

---

### Post by Vinze on 2005-09-23
[QUOTE=jimcooncat]Gee, Vinze, you were doing great, but I don't know about the last sentence. Is a trojan infection during a Linux app install any safer than on Windows? 

Compare deleting everything on my C: drive (that has no network shares mounted under that hierarchy) and rm -rf / (that has all my network shares mounted under it). The power of a Linux root account is awsome to behold.

Unless apt is using some kind of sandbox approach during installations (and I don't know if it does or not), I'd say no, your local system is quite well hosed no matter which OS you're using. If the network may actually be safer with Windows with this actual example -- but trojan writers do know how to browse SMB shares quite well.[/QUOTE]
 Well, I meant Linux is safer than Windows. The reason is because it by default doesn't let you work under root account :D . Well, exept for stupid Linspire of course ;) 

Btw, what do you mean with "you were doing great"?

---

### Post by jimcooncat on 2005-09-23
Vinze, I'm just trying to get a handle on good security practices myself. "You were doing great" with the advice, "Yes of course, but you do have to be consciously installing something. And if you're smart enough, you don't install anything from sources you don't trust. And I'm sure the Ubuntu and Debian reprositories widely satisfy your needs." 

And that's exactly the point I was trying to make. To me, Linux doesn't have any security advantages over Windows for the casual user if they're downloading installation files from some arbitrary place on the web, except that Trojans and spyware aren't that prevalent on Linux applications for reasons discussed before in this thread.

I think the biggest advantage we have here is that we have official repositories. If Microsoft provided a similar setup for third party apps (and people used it), users wouldn't have anywhere near the amount of problems in this regard; of course there's always the open/closed source argument as well.

Sorry to jump like that, I'm just a little jumpy lately about security in general.

---

### Post by Vinze on 2005-09-23
[QUOTE=jimcooncat]Vinze, I'm just trying to get a handle on good security practices myself. "You were doing great" with the advice, "Yes of course, but you do have to be consciously installing something. And if you're smart enough, you don't install anything from sources you don't trust. And I'm sure the Ubuntu and Debian reprositories widely satisfy your needs." 

And that's exactly the point I was trying to make. To me, Linux doesn't have any security advantages over Windows for the casual user if they're downloading installation files from some arbitrary place on the web, except that Trojans and spyware aren't that prevalent on Linux applications for reasons discussed before in this thread.

I think the biggest advantage we have here is that we have official repositories. If Microsoft provided a similar setup for third party apps (and people used it), users wouldn't have anywhere near the amount of problems in this regard; of course there's always the open/closed source argument as well.

Sorry to jump like that, I'm just a little jumpy lately about security in general.[/QUOTE]
 O, like that. Well, don't be fooled, I'm not such a long user of Linux, I just am interested in articles on this so that's were I got all the info from :P .

---

