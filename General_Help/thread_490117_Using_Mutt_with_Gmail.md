---
title: "Using Mutt with Gmail"
date: 2007-07-02
forum: General Help
---

### Post by andrew.46 on 2007-07-02
Hi,

 I would love some criticism, reviews, suggestions etc for a page I am in the process of "polishing up" that deals with setting up the email program Mutt to use Gmail as a relay:

[http://people.aapt.net.au/~adjlstrong/mutt.html](http://people.aapt.net.au/~adjlstrong/mutt.html)

 Thanks for your trouble,

           Andrew

---

### Post by 655 on 2007-07-18
This is exactly what I was looking for.  
I just scanned over the document briefly, but I intend to work my way through it this weekend.

As you say, it would be ideal to actually learn the workings behind these commands rather than blindly copy them from a tutorial.... but you've provided a wonderful springboard for what seemed like a vast expanse of insurmountable research.  

Once I read through it, if I have any criticisms I'll post 'em.

---

### Post by andrew.46 on 2007-07-18
Hi,

 Thanks for the thoughts:

> **655 said:**
>  [...] but you've provided a wonderful springboard for what seemed like a vast expanse of insurmountable research.  

Once I read through it, if I have any criticisms I'll post 'em.

 More research and time than I would care to acknowledge :-) I hope you will like Mutt as much as I do!

                     Andrew

---

### Post by 655 on 2007-07-21
Everything went off without a hitch, thank you.
I had been avoiding trying this because I was under the impression that getting specifically Gmail and the SSL certs and whatnot working with Mutt was difficult. 

It was a snap though... well, you did the leg work for me.

What are the ramifications of storing the password in a plain-text file, despite changing permissions on it?
Not overly concerned as this is a single-user machine but just curious.

Also, hard pressed to find anything that needs improvement in the guide, only this minor typo:
> 
...that will actually do this for you when you simply press "L". Place the following in your ~/.muttrc file:

macro index,pager **[COLOR="Red"]I[/COLOR]** '<shell-escape> fetchmail -v<enter>' 

That's an **I** in the phrase you wrote, not an **L**.  It's immediately self-evident, but just for completeness' sake I mention it.

Other than that, I honestly found it extremely intuitive; the writing style itself is easy to follow while being dense in details at the same time.   Good work.

---

### Post by andrew.46 on 2007-07-21
Hi,

 Thanks for your kind words! And especially thanks for picking up the unfortunate typo of "L" and "I" which I have now corrected.

 I was myself not keen on the setting up of the ssl certificates as I did not fully understand many of the guides available. Thanks to whoever packaged the repository OpenSSL package for including a certificate 'ready to go'.

**Correction**: *The gmail certificate material is actually in the ca-certificates package.*

 About password security I am not sure but you could certainly raise the issue with the fetchmail users group. My impression is that there _is_ a degree of insecurity to this technique. I would be interested to hear what they would say.

 Hope you are happy with mutt! I am glad my simple guide has been of help to you.

                  Andrew

---

### Post by 655 on 2007-09-27
By the way..............

Where can I go to research a way to automate the retrieval of mail in an open mutt client (i.e. running in a tty screen window) at timed intervals?

I should be looking for this myself but you have so earned my respect with your wonderful site and tutorials that I instinctively want to run to your for advice :oops:

I'm googling as we speak, though, I swear.

---

### Post by andrew.46 on 2007-09-27
Hi,

 I am immensely flattered:

> **655 said:**
> By the way..............

Where can I go to research a way to automate the retrieval of mail in an open mutt client (i.e. running in a tty screen window) at timed intervals?

I should be looking for this myself but you have so earned my respect with your wonderful site and tutorials that I instinctively want to run to your for advice :oops:

I'm googling as we speak, though, I swear.

 But I must disappoint you I am afraid as I don't know how to accomplish this :confused:. You can off course call a script from within mutt by typing in ! from a mutt window and calling a script from there. But as for the script ....

                 Andrew

---

### Post by 655 on 2007-10-03
That's ok - 
I thought of a better solution.
I'll just "script" myself to check it in the morning and at night manually, rather than obsess about automating everything. :-\"

---

