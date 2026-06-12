---
title: "pia cannot connect"
date: 2018-03-27
forum: General Help
---

### Post by jgw on 2018-03-27
ubuntu 116.04.4


My pia is connecting forever.  I submitted a request to fix it.  The reply was of no help at all.  I could not get by the 'disconnect' after pressing the icon (orange, the disconnect button does not disconnect).  Since this is a new installation, v78, I have not connected and have nothing to create a new vpn connection I am, basically, screwed. 

My hope is that I can get some help here.  I think I will also post this on the ubuntu forum just in case. 
I have one log: [https://pastebin.com/bfWuxUZD](https://pastebin.com/bfWuxUZD)

I have been running with pia for years with no problem then, suddenly, the thing could not connect.  I thought I would get some help from pia but, sofar, nothing useful. 

Any thoughts on this one would be appreciated.

thank you.....................

---

### Post by #&amp;thj^% on 2018-03-30
> **jgw said:**
> ubuntu 116.04.4


My pia is connecting forever.  I submitted a request to fix it.  The reply was of no help at all.  I could not get by the 'disconnect' after pressing the icon (orange, the disconnect button does not disconnect).  Since this is a new installation, v78, I have not connected and have nothing to create a new vpn connection I am, basically, screwed. 

My hope is that I can get some help here.  I think I will also post this on the ubuntu forum just in case. 
I have one log: [https://pastebin.com/bfWuxUZD](https://pastebin.com/bfWuxUZD)

I have been running with pia for years with no problem then, suddenly, the thing could not connect.  I thought I would get some help from pia but, sofar, nothing useful. 

Any thoughts on this one would be appreciated.

thank you.....................

From the terminal run:
```
/opt/pia/run.sh > /dev/null 2>&1 &
```
paste back the information shown.

And it shows that "PIA" is in your autostart, remove or uncheck it so it dose not want to run on startup.
I'm running the same version as you and have no problems.

---

### Post by jgw on 2018-04-20
Thank you for the reply and I apologize for not responding sooner.  Since then I have removed all of pia and then reinstalled it.  I have done this 2 times.  The first time I asked pia how to do it and they cleverly had me setup a pptp vpn connection and then, when I asked about openvpn they told me about 5 different things to do and that whole thing has been going on for about 2 weeks, with about 6 different tech people who didn't help at all.  I finally sent them a bunch of photos that documented, exactly, what I did and what happened and I never received a response.  Basically, pia support really sucks!  What I now have is an orange icon that infers that I am maybe/not really connected but my network connections tells me I am connected and running open vpn.  Anyway, that being the case I did as you asked and got (also went to /opt/pia to see what was there):
greg@movies:~$ /opt/pia/run.sh > /dev/null 2>&1 &
[1] 29814
greg@movies:~$ 
greg@movies:~$ cd /opt/pia
[1]+  Done                    /opt/pia/run.sh > /dev/null 2>&1  (wd: ~)
(wd now: /opt/pia)
greg@movies:/opt/pia$ ls
frontend  openvpn-32  openvpn_launcher.32  pia_manager  root_runner  run.sh
nwjs      openvpn-64  openvpn_launcher.64  rgloader     ruby

I have also added some photos that may be of interest.

---

