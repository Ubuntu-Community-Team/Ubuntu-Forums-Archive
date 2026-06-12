---
title: "Firefox and Self Signed or invalid SSL certificates"
date: 2008-07-07
forum: General Help
---

### Post by SpaceTeddy on 2008-07-07
Hi Folks, 

this is something that really, really drives me nuts. Whenever i try to open a page that is encrypted with a self signed certificate, firefox just give me an error page saying :** sec_error_untrusted_issuer**.
Now, i know this is because i don't have the proper root certificate, or the certificate was not signed properly.

The thing is - Most software comes with preinstalled, not properly signed certificates. How am i supposed to upload the proper Certificate if i cannot access the page in the first place. And using a non-ssl connection is far worse than temporarily using a cert that is not issued by a known CA (Let alone the fact i have about 100 CA's in my FF cache of which i know pretty none anyway...).

So, how do i make Firefox ASK me if i want to load the page anyway instead of just blocking me... Opera is usually my workaround - but it misses most of my plugins i need to for other tasks... 

any help is appreciated :)

---

### Post by jlrubin on 2008-07-07
Tools / Options / Advanced / Encryption / View Certificates

The "Servers" tab will let you add exceptions or import certificates. The "Authorities" tab will let you add new authorities.

---

### Post by cybaix on 2008-07-21
jlrubin,
I don't think you read his entire question. He wants to know specifically how he can get Firefox to just ask him if he wants to continue, instead of adding an exception for each page (which is a horribly long process).  I am in the same situation and would like to know a solution as well.

---

### Post by SpaceTeddy on 2008-07-21
yeppers... that's what i wanted to know. Besides, the firefox 3 in windows and mac still has the little warning window which lets you add an unknown ca to your trusted root ca's. In Ubuntu, this seems to be missing (for some reason... )

I am still using opera to navigate such pages... And i am still interested in any solution possible :)

thanks for any help in advance

---

### Post by jay019 on 2008-07-21
Thats weird as I added one today from Firefox 3. I thought it was blocking me but there was a button on the page that after clicking gave me the option to accept the certificate and get on with things.

---

### Post by SpaceTeddy on 2008-07-21
ok, this is odd. 
From what you said, i got the idea of creating a second a profile for my Firefox - and there the question is back if i want to add an unknown certificates. So this seems to be a problem with my profile rather than Firefox itself... However it managed to do that. The question is:
how do i tell my default profile for firefox to ask me again instead if blocking right away... 

If i figure something more out, i will post it.

---

### Post by cybaix on 2008-07-23
Hmm.. let me clarify on what I am looking for.  I DO have the button, however it is a 3-step process to add an exception and it is rather time consuming with the amount of self-signed certificates I encounter in one day.  I want a way to turn off the idiot proofing for certificates so that I can go back to the 1 button press of yestermonth so that I don't get carpal tunnel from the extra ~1000 clicks I have to make in a given day.

---

### Post by jimv on 2008-07-23
> **cybaix said:**
> jlrubin,
I don't think you read his entire question. He wants to know specifically how he can get Firefox to just ask him if he wants to continue, instead of adding an exception for each page (which is a horribly long process).  I am in the same situation and would like to know a solution as well.

It's like 3-4 clicks...unless his machine is doing something different than mine.  Besides, adding the exception is better in the long run, because you don't get prompted every time you go to the page.

---

### Post by jay019 on 2008-07-23
> **cybaix said:**
> Hmm.. let me clarify on what I am looking for.  I DO have the button, however it is a 3-step process to add an exception and it is rather time consuming with the amount of self-signed certificates I encounter in one day.  I want a way to turn off the idiot proofing for certificates so that I can go back to the 1 button press of yestermonth so that I don't get carpal tunnel from the extra ~1000 clicks I have to make in a given day.

Have you looked in about:config? I had a quick poke and not sure if this is what your looking for, but did find: security.default_personal_cert As I dont go to many self signed sites I cant tell you if this woks or not. Other than that maybe just go back to firefox2 as firefox 3 was created with the masses in mind and as we all know common sense is not really all that common.

Also, if you getting carpal tunnel from mouse clicks I suggest seeing a doctor and going outside more.

---

### Post by SpaceTeddy on 2008-07-24
i've just run through the config and changed about everything i could to figure out if it is any of these options. I also compared them to a firefox profile where it works and made it look the exact same - no difference.
To clarify the issue here, i have done a screenshot where you can see my problem. 

The Left Firefox window is my default profile which i use all the time. It is neatly configured and would be a pain to reset. That is also the one throwing the error. 

The right Firefox profile is called dummy. I just created that one. This one asks me the question i want it to ask.

In both windows i am accessing the same webmin site (first thing that came to mind when i needed an unsigned SSL cert). Why are they behaving differently ?

What i want is that the left windows does what the right one does. There must be something in the options somewhere...

I hope i have finally made myself clear... 
Thanks again for all the help :)

PS: sorry for everything being german. But i didn't want to change the entire language of my system for one screenshot :(

---

### Post by jay019 on 2008-07-24
Only thing I can suggest is doing a diff on your config files and try and find the difference that is causing the errors. Unless someone else has any ideas what it could be.

---

