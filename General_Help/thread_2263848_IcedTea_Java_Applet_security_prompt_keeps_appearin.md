---
title: "IcedTea Java Applet security prompt keeps appearing"
date: 2015-02-03
forum: General Help
---

### Post by Vesnog on 2015-02-03
First of all let me state that this issue has been bugging me for several months and I am not sure if this is the right subforum to ask this, if not please guide me accordingly. I am running Ubuntu 14.04.1 64-bit LTS with *OpenJDK Java 7 Runtime, IcedTea Web Control Panel, IcedTea Java Web Start and Icedtea Java Plugin(browser plugin)* installed. I am using *Firefox 35.0.1* and when I try to connect to the VPN service of my university I came across a prompt asking whether I am sure or not to run the application and it does not have a checkbox to retain when I click yes or no. I tried to configure this behaviour by running *IcedTea Web Control Panel* and you can see my settings in the attached screenshots. However, this did not work as intended apart from that I noticed that the IcedTea Web Control Panel does have different settings for the *root user* and an *ordinary user with sudo privileges*. Upon noticing that I tried changing the settings for the* root user*  too, yet there was no change I was bugged by the prompts persistently as before. Last but not least I posted this problem on the **IcedTea mailing** list where they suggested me to change the file **~/.config/icedtea-web/deployment.properties** as follows:

    ```
#Netx deployment configuration
    #Wed Feb 04 00:34:02 EET 2015
    deployment.manifest.attributes.check=false
    deployment.security.level=ALLOW_UNSIGNED
```

I tried all of these but none of these resolved my problem what may be my mistake I would be very glad if someone can help me on this issue. The first screenshot is the prompt that I always encounter and the rest are the settings for *IcedTea Web Control Panel* for a regular user. I posted all the settings in case they might be relevant to my problem.

---

