---
title: "Un authorized downloads even after quitting browser/Update Manager"
date: 2012-12-08
forum: General Help
---

### Post by sorc3r3r on 2012-12-08
Hi

I am using Ubuntu 11.10. I use Mozilla 17.0.1 as my browser. 

I have been noticing this incident for the past few days. 
Even when my browser is not downloading anything or if I have closed the Mozilla browser, the system monitor shows bytes being received. 
I checked the update manager: It shows that "package information was updated 2 hours ago" etc. So I assume that it is not the update manager which is trying to download something.

My question is

1)is it because of some virus? I have the UFW up and running. I haven't installed any other anti virus. Is it really required on Linux variants?

2)How can I see the details of what  UBUNTU trying to download?

3)If there are such downloads, does Ubuntu maintain a log of such events or downloads.

4)Is there any way to know to which location is the files being downloaded?

5)What should I do to prevent such downloads which are not initiated by the User by a command or other means.

I am using a 3G service to connect to the Internet and these unknown sending/recieving of bytes is taxing my bandwidth on the Internet.

++++++++++

Operating system : Ubuntu 11.10. Upgraded   from Ubuntu 11.04 via update manager
Browser:Mozilla 17.0.1

+++++++++++

Thank you!

---

### Post by sorc3r3r on 2012-12-08
And one more thing,I forgot to mention.
Every time such a download happens, I have to disconnect from the Internet," remove" the the 3G USB DONGLE from the laptop.
When I reconnect, the downloading had stopped and things are back to normal.
But
Simply disconnecting from the Internet and reconnecting doesn't seem to help most of the time.
](*,)
Only when I remove the dongle from the machine and connect it back, such downloading stops.
:-k

:confused:

---

### Post by lisati on 2012-12-08
*Thread moved to **General Help**.*

If you think your thread is in the "wrong" place, the forum staff don't mind if you use the "report" button to ask for the thread to be moved.

---

### Post by Kirk Schnable on 2012-12-09
You can use the package called **iftop** to monitor all active connections and data transferred in real time. This should be an effective way to figure out where bandwidth is going.

---

### Post by chadk5utc on 2012-12-09
Look at netstat -antp to see where your server is trying to call this may also help point you in the right direction searching the logs for additional information.

---

### Post by pompel9 on 2012-12-09
Not sure if this is correct. But here goes.

On windows there are always some communication, shown as packages downloaded/uploaded. What I am talking about is a few kb here and there. Nothing major.

I have not checked this on Ubuntu, but I would think it works the same way.

This is just a theory, but I think does packages is actually the ISP that communicates with your PC and modem/router.

---

### Post by Kirk Schnable on 2012-12-09
> **pompel9 said:**
> Not sure if this is correct. But here goes.

On windows there are always some communication, shown as packages downloaded/uploaded. What I am talking about is a few kb here and there. Nothing major.

I have not checked this on Ubuntu, but I would think it works the same way.

This is just a theory, but I think does packages is actually the ISP that communicates with your PC and modem/router.

Well, I was hoping that with iftop he'd be able to uncover the source of the communication. What you're saying is somewhat truthful. 

@sorc3r3r: How much ghost data are we talking about here? 50KB, 5000KB, 50MB?

---

### Post by Statia on 2012-12-09
Hi, you say you are not downloading anything, but are you for instance logged in in your Gmail account? With the Google Talk plugin, this causes some communication to go on, to see who is online, etc. Same goes for Skype.
I had something similar, it turned out it was a Superkaramba applet that shows my external IP that checked that IP once a minute. So if you have something like Conky running, or some other applet that shows your external IP, there's another possible culprit. Same for apps that show things like the weather, or stock quotes.

---

### Post by sorc3r3r on 2012-12-10
>  @sorc3r3r: How much ghost data are we talking about here? 50KB, 5000KB, 50MB? 

5 MB or more . At times even more.

==

> Hi,  you say you are not downloading anything, but are you for instance  logged in in your Gmail account? With the Google Talk plugin, this  causes some communication to go on, to see who is online, etc. Same goes  for Skype.
I had something similar, it turned out it was a Superkaramba applet that  shows my external IP that checked that IP once a minute. So if you have  something like Conky running, or some other applet that shows your  external IP, there's another possible culprit. Same for apps that show  things like the weather, or stock quotes. 	  	

Basically, I use only Gmail. I check it on Basic HTML format. So there is no other plugin running. 
I use the standard installation of Ubuntu 11.10.  I have not installed any other applications from the software center etc etc. Just the VLC player and the codecs.
Also
I don't have any other applications running like empathy or evolution.

===

> Not sure if this is correct. But here goes.

On windows there are always some communication, shown as packages  downloaded/uploaded. What I am talking about is a few kb here and there.  Nothing major.

I have not checked this on Ubuntu, but I would think it works the same way.

This is just a theory, but I think does packages is actually the ISP that communicates with your PC and modem/router. 	

On Windows, yes..I have seen such data being received. Who knows what is what.!!

But Well, on Ubuntu, I have never seen data streaming like this before. When the browser is inactive or no other application is using Internet, the bytes recieved will be 0 or something very insignificant  I agree with you , It usually would be the ISP communicating with the modem.
Anyway,
Here Iam talking about quiet significant amount of data getting downloaded to the machine.
===

>  		You can use the package called **iftop** to monitor all active  connections and data transferred in real time. This should be an  effective way to figure out where bandwidth is going. 	

Sure thing. I will try  the iftop. Hope I can figure out the source.

Thank you :)

===

---

### Post by sorc3r3r on 2012-12-10
> **lisati said:**
> *Thread moved to **General Help**.*

If you think your thread is in the "wrong" place, the forum staff don't mind if you use the "report" button to ask for the thread to be moved.

Sure thing. I didn't know about this.

---

