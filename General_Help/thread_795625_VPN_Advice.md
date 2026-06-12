---
title: "VPN Advice"
date: 2008-05-15
forum: General Help
---

### Post by Squizz on 2008-05-15
Hi there,

I'm going to be designing a php/mysql project that will run from a local server.   This will be inaccessible through the internet.  The server itself will be a LAMP server using Hardy - but the users will be using windows.

Whilst in the office, then all will be dandy, but if we want to work from home then there's a problem.

I realise that I could just make the project available over the internet, but the information is sensitive, so I'd rather a VPN solution.

I'd like some advice on choosing some open source VPN software that will be compatible and reliable with Ubuntu and also Windows XP/Vista.

Any advice would be gratefully received.

Thanks

---

### Post by Monicker on 2008-05-15
Openvpn would be a good choice.  We use it a work.  Runs on both linux and windows.

---

### Post by Squizz on 2008-05-15
Looks good, will install on a development server and test it out :)

Any other recommendations?

---

### Post by bodhi.zazen on 2008-05-15
As far as I know all the VNC servers in Hardy work with the tightVNC viewer on a windows client. At least the 4 I have tried have all worked.

I advise you tunnel over ssh :

[uwiki]VNCOverSSH[/uwiki]

---

### Post by Squizz on 2008-05-15
> **bodhi.zazen said:**
> As far as I know all the VNC servers in Hardy work with the tightVNC viewer on a windows client. At least the 4 I have tried have all worked.

I advise you tunnel over ssh :

[uwiki]VNCOverSSH[/uwiki]

I'm not sure if I've misunderstand what you mean, or didn't explain what I plan to do properly?  Basically, the Windows users will open a browser and navigate to [http://local-server/](http://local-server/) and be able to access the application that is hosted on the ubuntu machine.  If the users use the VPN connection from home or something, they should then be able to just open their browser and use [http://local-server/](http://local-server/) as if they were sat at their desks in work.

I hope what I plan to do is feasible too!

---

### Post by Monicker on 2008-05-15
> **Squizz said:**
> I'm not sure if I've misunderstand what you mean, or didn't explain what I plan to do properly?  Basically, the Windows users will open a browser and navigate to [http://local-server/](http://local-server/) and be able to access the application that is hosted on the ubuntu machine.  If the users use the VPN connection from home or something, they should then be able to just open their browser and use [http://local-server/](http://local-server/) as if they were sat at their desks in work.

I hope what I plan to do is feasible too!

Yes, it definitely is.

---

