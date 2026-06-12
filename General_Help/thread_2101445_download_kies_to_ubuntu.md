---
title: "download kies to ubuntu"
date: 2013-01-04
forum: General Help
---

### Post by roanantelope on 2013-01-04
Hi ubuntu,
I need to download kies to use with my samsung phone. It worked well with windows. Will it work with ubuntu please?

regards,
roanantelope

---

### Post by jvano on 2013-01-04
as far as i know Samsung Kies is not available for Linux / Ubuntu.

You can try two diferent ways.

1 run it from Wine, wine is a program to run windows programs over Linux .
2 Install Virtual Box and use a virtual Windows machine to run Kies.

---

### Post by timgood on 2013-01-04
If all you want to do is transfer files to and from your phone then:
 ```
sudo apt-get install gmtp
``` 
and then run gmtp from the dash. It's a great graphical android file transfer program and works well with my Samsung Tablet and my Nexus 4 phone.

---

### Post by roanantelope on 2013-01-05
> **jvano said:**
> as far as i know Samsung Kies is not available for Linux / Ubuntu.

You can try two diferent ways.

1 run it from Wine, wine is a program to run windows programs over Linux .
2 Install Virtual Box and use a virtual Windows machine to run Kies.

Thank you Jvano. Where do I download wine please?

---

### Post by timgood on 2013-01-05
> **roanantelope said:**
> Thank you Jvano. Where do I download wine please?

You can install Wine from the Ubuntu Software Centre or from the terminal:

```
sudo apt-get install wine
```

---

### Post by roanantelope on 2013-01-10
Thank you timgood, I will try this at the weekend

regards,
roanantelope.

---

### Post by Hylas de Niall on 2013-01-10
Doesn't the phone show up as usb storage? Mine does but only with the proper Samsung cable.

---

### Post by alberto-tornaghi on 2013-11-29
You don't need to download anything to use Kies in a Linux machine. 
Your computer and mobile must be in the same wifi network. 
Open kies in your mobile. It will present you an URL number, something like [http://192.168.0.95:8080](http://192.168.0.95:8080)
Type this in the adress area of your browser.
That's it. 
Go on. Be happy.

---

### Post by Dave_Alexander on 2013-12-12
Thank you Alberto, i will try when I get home. this network is too slow. Xmas blessings to you as well

Regards,
Dave.

---

### Post by Sleepy-zz-John on 2014-05-16
> **alberto-tornaghi said:**
> You don't need to download anything to use Kies in a Linux machine. 
Your computer and mobile must be in the same wifi network. 
Open kies in your mobile. It will present you an URL number, something like [http://192.168.0.95:8080](http://192.168.0.95:8080)
Type this in the adress area of your browser.
That's it. 
Go on. Be happy.
This looked like a perfect solution but it hasn't worked for me,  so maybe I'm missing something?  

I typed [http://192.168.1.4:8080/](http://192.168.1.4:8080/) into my SeaMonkey browser on 12.04 and it gave me 

```
Failed to Connect

The connection was refused when attempting to contact 192.168.1.4:8080.

Though the site seems valid, the browser was unable to establish a connection.
```

Now I couldn't open or install ***kies*** on my android because it appears to be sw that can only be installed in a mac or winwoes,  but I was able to determine
that my android's IP  was 192.168.1.4 by interrogating my wifi router.  

So my question is what exactly do I have to install in my android to allow me to gain access to its files via wifi? 

Does the ***kies*** installed in a mac or win device somehow access an android differently to how my Seamonkey does via wifi?

---

### Post by kissor-samanta on 2014-11-24
kies not getting downlodded for ubuntu

please thread in 2 load samsung kies

Please allow to thread in to download kies

---

### Post by Elfy on 2014-11-24
Please do not constantly post to a thread - edit it instead. 

Also - the last 2 comments make no sense at all.

---

