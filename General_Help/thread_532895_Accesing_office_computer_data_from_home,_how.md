---
title: "Accesing office computer data from home, how?"
date: 2007-08-23
forum: General Help
---

### Post by jofre on 2007-08-23
Hi everyone,

I need to access data I have in my office(ubuntu) computer from my home computer. I am obviously not exactly a network guy, so I need advice. 

Should I use ftp, Samba, or something else? 

The websites I found so far seem to deal with local networks, (next door office), but not for outside (I hope I am not saying anything stupid...)

Thank you Ubunteros! (Spanish word for people who use Ubuntu ;-)  )

---

### Post by Seisen on 2007-08-23
If they are both Ubuntu computers you could use NFS which is faster than Samba.

---

### Post by Bohdie on 2007-08-23
NFS would be a good bet, but the issue I think would be of concern is how are you accessing your office. To put business intellectual property out for everyone to see, I would think would not be the first choice. I would check with your Network Admin has any VPN ability. If this is not a big issue, I would suggest something like openVPN (another reason for Linux in the workplace). It may have to be placed in a less secure domain of your offices network. Also I should be monitored strickly to ensure what is being made available on datastores and filesystems. 

If your company has an issue with this, you may have to setup something in reverse and open your home network.

---

### Post by jofre on 2007-08-25
Thanks for the reply.

My intention is to share data with myself and other people that are working in different places. I work in the university so, I would not like the data to be publicly available, but just to some people which I could provide with a user name and a password.

I download things constantly from internet, it is really that hard to setup something similar but with a user name and a password?

May be is not as straight forward as I thought. I am doing this more for as a secondary project, so I really do not want to bother the network guy of the university. Also I would not mind to learn a bit about networks

Apologies in advance  for my ignorance :)

---

### Post by callan79 on 2007-08-25
> **jofre said:**
> My intention is to share data with myself and other people that are working in different places. I work in the university so, I would not like the data to be publicly available, but just to some people which I could provide with a user name and a password.

Well, if we assume that :

(1) your computer at the Uni has a real IP Address on the Internet (i.e. not a private IP behind a firewall)
and
(2) You have permission from the Uni to do so

Then I'd probably set this up using FTP or Samba, depending on what you're trying to do.

FTP is great because it requires a username and password and basically every computer in the world would have access to FTP, but it would require some setting up on your end.

If the people you're dealing with want to have the shared files accessible easily though, i.e. through Ubuntu's PLACES menu or through Windows MY COMPUTER, then samba shares are the way to go.

Can you confirm if your computer at Uni is directly contactable from the Internet, or if you're behind a firewall?

For example - at work, my computer is 219.90.x.x, which is visible directly from the Internet, so sharing files is easy. At home though I'm on 192.168.7.22 which is behind a firewall and would therefore need the network admin to open some holes in the firewall for you. In the case of home access this is easy. In the case of Uni/Work, perhaps not so easy ....

Cheers
Callan

---

### Post by louieb on 2007-08-25
If it were me I would install openssh-server. Then you would need to set up a user account for those you wish to grant access. To get on the machine remotely you would need an ssh client Ubuntu has one by default or Putty in windows. To log-in remotely using the client the user would have to Know the IP of your office machine. 
 
callan79 FTP option would be easier for your users to use.

---

### Post by jofre on 2007-08-25
I am at home now, so I would not being able to try your suggestions until Monday. I do not know if I am or I am not behind a firewall, but I know that I need a manual configuration of a proxy. 

Thanks again, I will let you know how it goes.

Jofre

---

