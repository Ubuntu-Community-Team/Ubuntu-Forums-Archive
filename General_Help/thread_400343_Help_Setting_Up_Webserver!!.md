---
title: "Help Setting Up Webserver!!"
date: 2007-04-03
forum: General Help
---

### Post by Atrio05 on 2007-04-03
Hi I'm gonna need someones help to get my webserver forwarded properly. i can't seem to get my router to forward to port 80 properly and that means no one can see my site except the computers in my network. my router is a Buffalo WHR-G54S.

someone please help me out!

thanx!

---

### Post by kevpatts on 2007-04-03
I haven't used that router before but a lot of Routers don't let you forward port 80. They tend to use it for they're own configuration interface.

---

### Post by FluffyElmo on 2007-04-03
Many ISPs block port 80 for residential accounts, as well as port 25. Try setting it up on a different port, say port 8080 and if it works then that's most likely your problem.

---

### Post by Atrio05 on 2007-04-03
what do you mean? so i can acess my site from another computer not on my network with a port other than port 80?

---

### Post by pppetter on 2007-04-03
sure, if you can't get port 80 to work, just edit /etc/apache2/apache2.conf, look for > Listen 80
And change it to whatever you are comfortable with, and then forward that port on your router. 

There's just one less fun thing about it, you'll need to enter IP:PORT or DOMAIN:IP instead of just IP or DOMAIN. Of course with some dns services like noip.com can handle that for you, so you just need the DOMAIN and not DOMAIN:PORT.

---

### Post by Atrio05 on 2007-04-03
ok i understand how to do the first part, but i don't know what you mean here "There's just one less fun thing about it, you'll need to enter IP:PORT or DOMAIN:IP instead of just IP or DOMAIN. Of course with some dns services like noip.com can handle that for you, so you just need the DOMAIN and not DOMAIN:PORT."

---

### Post by Scunizi on 2007-04-03
When you go to most normal site you type [www.somethinghere.com](www.somethinghere.com). To get to your server you have to put in your IP address from the WAN side (what your ISP is providing your router) but you'll also have to include your port.  For instance, inside the lan you can access your server by http:://localhost:80 or 192.168.0.100:80 (depending on what the ip address is of your server.  From out in the wild web people will enter 75.205.22.365:portnumber  (it's hard to see the colon between the IP address and the port number but you have to include it)  or whatever your actual IP address is.

---

### Post by Atrio05 on 2007-04-03
so theres no easy way to figure out if i can open port 80? like to see if my isp is blocking it or to see if my router will forward it?

do you want to see a picture of my routers config page? 

some one help me out here please!

---

### Post by Scunizi on 2007-04-03
Just figure on not using port 80 and change it to 8080 or 8081 or etc  etc  etc.. then get on with what you're doing.

---

### Post by Atrio05 on 2007-04-03
well i used the network tools in system>administration and used the port scanner and it said my port 80 and port 22 are open. so i don't see why you can't help me figure out why my site won't show up on computers not on my network?

---

### Post by Atrio05 on 2007-04-04
so no one can help me on this?

i'm trying to set it up with dyndns.org and my port 80 is open so why is my site not showing up?

---

### Post by Atrio05 on 2007-04-04
any ideas anybody?

---

### Post by Atrio05 on 2007-04-05
ok is there any How to's on setting up apache correctly i think thats my problem i don't think i set it up right.

thanx!

---

### Post by svaucher on 2007-04-05
Ok, I'm not too sure I understand what you've done and what you verified. So here we go again:
 
1/ If Apache works on your LAN, it's probably set up correctly.
2/ Configure your router to use port 8080. Call a friend with an Internet connection and tell him to go to your site (from the WAN) http://<ip_address>:8080/. I don't know of any ISPs that don't allow connections to 8080, so it *should* work.
3/ If that works, that means you know how to configure your router + Apache correctly. Do the same now with port 80. If that fails, your ISP is blocking port 80. You'll have to live with it.

---

### Post by Atrio05 on 2007-04-05
do i need to restart the apache server when i change /etc/apache2/ports.conf to listen oin port 8080?

---

### Post by Atrio05 on 2007-04-05
well i did what you guys suggested and forwarded my router to port 8080 and then tested to see if i could reach the site on my girlfriends computer (not on my network) and it did not work. i even tested it with the :8080 after the URL and tried it with :8080 after the ip address. 

and i have confirmed that my ISP Epix Jack Flash does not block any ports so i would really appreciate some help figuring out why i cannot reach my site on the internet! is there any thing i need to show you to help figure it out like maybe my router config screen because in my opinion i don't think i'm setting up the port forwarding part right.

well any help on the subject would be great!!

thanx!

---

### Post by gavinjb on 2007-04-05
Just a thought, the machine you have running apache on is it configured to use a static ip address, as if not the ip address has a chance of periodically changing.

I have never used a buffalo, but have used USR, Netgear & BT and all I have ever had to do is set port 80 to forward to the IP for the PC that apache is running on.  On some routers I found that I have had to reboot before it took affect, but I would have thought you would have tried this.

---

### Post by Atrio05 on 2007-04-05
i don't think that it is set up with a static IP address. But i use dyndns.org i think it keeps track of the IP address's for you. Not sure though dont quote me on that.

edit:
i just checked wikipedia, dyndns is a dynamic DNS host. which means it will keep track of my ip address's for me.

---

### Post by Atrio05 on 2007-04-05
bump ! !  ):P

---

### Post by Atrio05 on 2007-04-05
here are some pictures of my router settings the first one shows the main window and the second shows the port forwarding section and the third one shows Network Address Translation section 

thought maybe some of these would help someone help me!!

---

### Post by Atrio05 on 2007-04-06
bump ! !  ):P

---

### Post by Atrio05 on 2007-04-06
bump!!

---

### Post by Atrio05 on 2007-04-06
BUMP.. Im gunna keep bumping untill i get some answers here :twisted:

---

### Post by Subban on 2007-04-06
Have you considered checking any support or forums that Buffalo may have ?

You have said that Apache was is working inside  your own network, the problem is with your router? If that is the case then perhaps speaking with the routers support may get you the answers you need.

---

### Post by Atrio05 on 2007-04-06
ok well i guess i can give that a try but i doubt they will be able to help.

---

### Post by jeffathehutt on 2007-04-06
Is apache running on a seperate computer, or is it on the computer you are using to access the router's configuration?

---

### Post by dguitar on 2007-04-06
> **Atrio05 said:**
> i don't think that it is set up with a static IP address. But i use dyndns.org i think it keeps track of the IP address's for you. Not sure though dont quote me on that.

edit:
i just checked wikipedia, dyndns is a dynamic DNS host. which means it will keep track of my ip address's for me.

Yes they do keep track of your PUBLIC IP ADDRESS, not your Computer's IP Address.

I looked at the images you attached.

I'm guessing your computer has the 192.168.11.2 IP address. 

First try this, [http://192.168.11.2:8080]("http://192.168.11.2:8080") or [http://192.168.11.2]("http://192.168.11.2") if you haven't changed the port on your web server. If the page comes up, then continue, if not, something is wrong with apache. 

Go back into your router. Based on what I see, you don't need to change the port in apache, just do WLAN Port 8080 to Lan Port 80 on IP Address 192.168.11.2. (Unless you have changed the port in apache, then just forward it to that port)

Now, go to some place like [http://whatismyipaddress.com]("http://whatismyipaddress.com"), Take the IP address you see there, go to your browser type in http://<insert ip address from page>:8080

If none of that works, post back here with your findings and maybe I can offer more help.

---

### Post by Atrio05 on 2007-04-06
ok i will try to get all that for you after i get out of work tonight ok.

thank you for helping!

---

### Post by dougfractal on 2007-04-06
> **dguitar said:**
>  
Now, go to some place like [http://whatismyipaddress.com]("http://whatismyipaddress.com"), Take the IP address you see there, go to your browser type in http://<insert ip address from page>:8080


I don't know if it just my adsl router but I can't connnect(forward) to my external IP from inside my LAN.   I have to add my URL to my /etc/hosts.

To test your WLAN you would need to use an external proxy
i.e  [http://www.freeproxyserver.net/](http://www.freeproxyserver.net/)
then enter your URL:8080

Your NAT looks alright is your 192.168.11.2:8080  working?

---

### Post by Atrio05 on 2007-04-06
hey do you think my speed stream 4200 dsl modem would need to be forwarding to port 80 along with my buffalo router?

---

### Post by dougfractal on 2007-04-06
> **Atrio05 said:**
> hey do you think my speed stream 4200 dsl modem would need to be forwarding to port 80 along with my buffalo router?

Try this site
[http://www.techsupportforum.com/networking-forum/modems-cable-dsl-satellite/139931-my-messed-up-network-setup-modem-router-please-help.html](http://www.techsupportforum.com/networking-forum/modems-cable-dsl-satellite/139931-my-messed-up-network-setup-modem-router-please-help.html)


Am I right in thinking 
stream 4200 dsl modem is connected to ISP, and is DHCP server for your network.
then setup forwarding on it.
remove forward from your  buffalo router (not needed i think).
It looks like you can keep everything port 80. (reset apache[2].conf to 'Listen 80'.

---

### Post by Atrio05 on 2007-04-09
i really need some help here i tried just port forward on the dsl modem and just on the router and on both and still the site does not work can some one please help me out?

---

### Post by FluffyElmo on 2007-04-09
First, I think your DSL modem must be set to forward the port to the IP of *your router*. This will be the WAN IP Address listed somewhere in the router config panel. Your router must then forward the port to the IP address of your PC.

If this is confusing, first try removing the router from the setup and connecting your PC directly to the DSL modem. Forward the relevant port to your PC IP and if that works then look at reintroducing the router.

In reading the previous posts, I'm having a lot of trouble knowing what you've actually done and where you are in the debugging process. If it still isn't working  after trying the above could you please answer the following couple of  questions. I'm not trying to be glib, they'll help everyone understand the problem better since we don't know what you have tried.

1a. If you enter *[http://localhost:8080]("http://localhost:8080")* and [http://127.0.0.1:8080/]("http://127.0.0.1:8080/") in Firefox on the PC running Apache do you see your web page?
1b. If you enter *[http://localhost]("http://localhost/")* and [http://127.0.0.1/]("http://127.0.0.1/") in Firefox on the PC running Apache do you see your web page?

2. Go to [http://whatismyip.org]("http://whatismyip.org"). Copy the address and from a PC outside your network try *http://<IP>:8080* and *http://<IP>/* in Firefox (replace <IP> with the address from whatismyip.org). What do you see? Do you see your web page for either of them? 

Completely ignore the dynamic DNS stuff for the moment, get it working using IP addresses and worry about domain names later....

---

### Post by Atrio05 on 2007-04-11
so would it help me in any way to put my DSL modem in bride mode and then still use my router?
because i kinda need my router i have like 4 computers that i have to connect to it.

---

### Post by Atrio05 on 2007-04-11
ok i got my port 80 working but is there anyway that i can block up port 80 on all the other computers on the network because i don't want them exposed!

---

### Post by Atrio05 on 2007-04-12
> **Atrio05 said:**
> ok i got my port 80 working but is there anyway that i can block up port 80 on all the other computers on the network because i don't want them exposed!
 ok i did get port 80 to be open but my page was still unreachable from any computer on the internet. can some one please help me out this is so confusing it's driving me crazy!! :confused:

---

### Post by FluffyElmo on 2007-04-12
What exactly is working? There are a bunch of things that could be mis-configured but without knowing _exactly_ what you've done and what the result was we can't narrow the options down.

For now I'd still suggest removing the router temporarily and getting forwarding to work with just the one computer connected directly to the modem. This will cut down on the number of things that could be wrong and you can then reintroduce the router and deal with any issues it causes.

---

### Post by Atrio05 on 2007-04-12
ok i will try that tomm. i kinda figured it out today but it turns out i put the wrong ip adress in so it opened port 80 but forwarded it to the  wrong ip adress(i accidently forwarded it to the modem config) i don't know what happened exactly.

---

### Post by Atrio05 on 2007-04-12
ok i have now gotten it to the point where my port 80 is open and i think it should work but i need some one to test it so here is the link to whats supposed to be my [test site]("http://ourportal.dyndns.org") so can someone post back and tell me if anything loads when they click there. 

i have the router dissconnected so right now it's just the server hooked to the speedstream modem with port forwarding enabled.

---

### Post by FluffyElmo on 2007-04-12
Yes, the page loads from here.

---

### Post by Atrio05 on 2007-04-12
ok well than i kno what the problem is then it's my stupid router when i hook it back up it stops access to port 80 and even though i try to port forward it it still doesn't open it.

can you help me now i can shows you pictures of exactly what i do in my routers config and my speedstream. am i suposed to forward to the server on both  one what?

---

### Post by FluffyElmo on 2007-04-12
On the modem forward the port to your router, this is probably already set up. On the router you then forward port 80 to the computer IP and in theory it should work...

---

### Post by Atrio05 on 2007-04-12
what ip do i forward from the modem to the router the ip  use to edit the routers config?

---

### Post by Atrio05 on 2007-04-12
i get confused on my router when i get to this page what exactly do i put? i allways feel that i put the wrong things in the wrong spots.

---

### Post by FluffyElmo on 2007-04-12
You shouldn't have to change anything on the modem. If it was forwarding to the computer correctly then it will forward to the router the same way. Just connect it to the routers WAN port. 

Then on the router you want to forward port 80 to the (internal) IP address of the computer you're using to serve the web pages. That should do it, if you get the router config panel instead of your site then maybe your router won't forward port 80 as you want...

---

### Post by FluffyElmo on 2007-04-12
Just saw the screen shot, it looks correct assuming that 192.168.11.2 is the IP address of the server. There should be a panel in the router config that lists all the connected computers. Double check that the computer is connected and has that IP address.

---

### Post by Atrio05 on 2007-04-12
can you test the [site]("http://ourportal.dyndns.org") agian and make sure all the links work. because i clicked  on one and it took me to my modem config page.

---

### Post by FluffyElmo on 2007-04-12
It's working here, I tried all the links.

---

### Post by Atrio05 on 2007-04-12
well why when i click on lets say the pictureportal link it goes right to my modem config?

---

### Post by FluffyElmo on 2007-04-12
Probably because you're on the LAN. Internal requests on port 80 probably automatically go to your router config. You can try changing the port your router config runs on if that is possible, or just use the internal IP to access the site from the LAN.

---

### Post by Atrio05 on 2007-04-12
do you know how i can change the port the modem config runs on?

---

### Post by Atrio05 on 2007-04-12
so are my other computers going to be at risk because i have port 80 open?

---

### Post by Atrio05 on 2007-04-12
can anyone answer me?

---

### Post by Kinslayer on 2007-04-13
Having port 80 open for a server shouldn't be a problem for your other networked computers.  To check from outside, I used to use [http://anonymouse.org/](http://anonymouse.org/) until I got a different router (one that allowed mysite.foo to be a visitable address from the server).

---

