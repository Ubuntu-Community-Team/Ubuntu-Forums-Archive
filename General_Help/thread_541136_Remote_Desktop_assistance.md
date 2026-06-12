---
title: "Remote Desktop assistance"
date: 2007-09-02
forum: General Help
---

### Post by onegreenparker on 2007-09-02
I am setting up an Ubuntu machine that I will need to look after remotely.

I have looked through the forums for a basic howto on this subject, but I keep coming up against all sorts of obstacles. I´ve outlined below is what I have, some advice on this would be great.

1) The machine I need to control is running Dapper
2) It will have a dynamic IP address
3) The machine I will be using is running Fiesty
4) It too will have a dynamic address 
5) Security is not too much of an issue (perhaps when I get more ambitious I´ll tackle the security)

I think something simple will help plenty of other newbies

Thanks
Ian

---

### Post by PilotJLR on 2007-09-02
1. Make a free account at dyndns.org for the machine you need to control.
2. Install "inadyn" on the dapper computer you need to control (howto's on the dyndns.org site)
3. Set a static IP address for the dapper computer
4. Turn on Remote Desktop sharing under the System menu
5. On the router used where the dapper machine is, forward TCP port 5900 from the router to the dapper computer's static address from step 3
6. Connect to the dyndns.org account you created from elsewhere as you wish...

---

