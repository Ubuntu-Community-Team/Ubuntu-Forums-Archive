---
title: "Hotmail on ubuntu"
date: 2006-12-29
forum: General Help
---

### Post by ZERO_SHIFT on 2006-12-29
When trying to connect to my Hotmail account I get the following message in firefox:

> Unable to connect

      

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at login.live.com.

        


        
        


    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.




      


      

Please advice.

Thanks in advance.

---

### Post by ~LoKe on 2006-12-29
But everything else works?

Type this in the terminal:
> ping 64.4.33.7
If it's not connecting, contact your ISP and ask them if they're having DNS issues.

---

### Post by mrphd on 2006-12-29
Can you connect to other websites?

---

### Post by ZERO_SHIFT on 2006-12-30
I can connect to other sites just not Hotmail.

I got this:

zaid@zaid-laptop:~$ ping 64.4.33.7
PING 64.4.33.7 (64.4.33.7) 56(84) bytes of data.

???

What is wrong?? There is no problem in Windows whith connecting to Hotmail?

---

### Post by mjrclark on 2006-12-30
Hotmail on firefox 2 works for me. However, login.live.com resolves to a different IP than that given for me. Also, all pings fo not work to any of the hotmail sites- I think they must have disabled ping (stp packets or something, I forget the exact acronym).
To see if it is DNS issues I would recommend doing the following
ping login.live.com
then key ctrl and c at the same time.
If an IP address appeared next to the name, then DNS is working at least at some level. It is possible that MSN's servers have gone down for you area of the internet.

---

### Post by fredster001 on 2006-12-30
I dont know what the problem is, but i get very strange fonts from the hotmail page's whenever i use ubuntu. Anyone know why?

---

### Post by ZERO_SHIFT on 2006-12-30
This is what I got:

```
aid@zaid-laptop:~$ ping login.live.com
PING login.live.com.nsatc.net (65.54.179.248) 56(84) bytes of data.

--- login.live.com.nsatc.net ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms


```

Any ideas?

---

### Post by fragos on 2006-12-30
Get yourself a free gmail account and you'll have none of theses problems.  Hotmail comes from Microsoft and by definition evil.

---

### Post by ZERO_SHIFT on 2007-01-01
I have the same problem with my Gmail account!!!

Has anyone encountered the same problem??

---

