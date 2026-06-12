---
title: "Firestarter Custom Configuration - help plz"
date: 2007-09-21
forum: General Help
---

### Post by dornik on 2007-09-21
HI all.
Firstly, I am new to linux/ubuntu. I have got ubutu 7.04, Feisty Fawn up and running without any issues and have been using it for 3 days so far. I have also got Firestarter 1.0.3 up and running a short while ago but I am having an issue configuring it the way I would like. Heres the problem. 

When i try to create a new rule for inbound (or outbound) traffic policy, I am offered "default" ports. For example, if I want to add a rule for Bittorrent, I am "forced" to use the default ports 6881-6889. If I over ride this to something else, (say 7000), the "name" of the service changes to "Afs3-fileserver".

While I do understand that I can use another port thats not assigned to anything, I want to know if theres any way to override this annoying behavior on the part of firestarter?

As a windows user who has been using Zone Alarm for years, I have always been able to map any port I wanted to any service/application. Cant I do the same thing with Firestarter?

If not, will bit torrent still work using 7000 as long as thats the port mentioned for use in the bit torrent client itself even though Firestarter may state the service is reserved for "Afs3-fileserver"? Or will it deny bit torrent access to the port? What is "Afs3-fileserver" anyway? 

Why doesnt Firestarter allow a user to over ride default values? I just dont get it. Any help would be appreciated.

Thanks in advance.
Dornik

---

### Post by Enohc on 2007-09-21
Don't worry about the name.

Firestater blocks TCP/UDP ports, not apps. Just write 7000 in the port field if you want to, the name of the rule doesn't make any difference.

Anyway, In Firestarter 1.0.3 (the one that I have) you can edit the name of the rule after a name is suggested. So if I write 21, name will change to FTP but then I still can change the name.

Hope it helps.

---

### Post by dornik on 2007-09-22
Hello Enohc 
Did as you suggested and its working great! :)
Thank you for your help .

---

