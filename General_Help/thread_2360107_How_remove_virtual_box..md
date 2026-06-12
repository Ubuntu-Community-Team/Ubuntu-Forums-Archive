---
title: "How remove virtual box."
date: 2017-05-01
forum: General Help
---

### Post by rosswmcgee on 2017-05-01
I removed virtual box in synaptic but noticed much left behind and synaptic does not allow removal. Is there a reason for that? Or is there a terminal option for

complete removal? 

I am using 16.04lts. 

ran this command and everything is still there in synaptic.

sudo apt-get remove virtualbox virtualbox-qt && sudo apt-get autoremove

---

### Post by &amp;KyT$0P# on 2017-05-01
Does this help? -
```
sudo apt-get purge virtualbox virtualbox-qt && sudo apt-get --purge autoremove
```

---

### Post by ian-weisser on 2017-05-01
> **rosswmcgee said:**
> I removed virtual box in synaptic but noticed much left behind and synaptic does not allow removal.

Please be specific about what is left behind.
What do you mean 'does not allow'? Please be detailed.

---

### Post by rosswmcgee on 2017-05-02
Virtual box 5.0 in synaptic will only accept installation not removal. If you check the boxes only installation ever box pertaining to Virtual box is the same way. 

Maybe It was there to begin with. I had downloaded Virtual box and installed via a web link on this forum perhaps that was what was removed when i used the 

terminal commands above? Maybe I need to do nothing? It took about 15 minutes to remove it via terminal. I am just not sure what if anything needs to be done?

---

### Post by ian-weisser on 2017-05-02
> **rosswmcgee said:**
> Virtual box 5.0 in synaptic will only accept installation not removal. If you check the boxes only installation ever box pertaining to Virtual box is the same way.

Sounds like Virtualbox is removed, though your description has room for misinterpretation.

What leads you to believe that it's not removed? What are you seeing?

---

### Post by rosswmcgee on 2017-05-02
The fact that it's still listed in synaptic. And that there is no option to remove it only to install it.

---

### Post by howefield on 2017-05-02
> **rosswmcgee said:**
> The fact that it's still listed in synaptic. And that there is no option to remove it only to install it.

Can you screenshot what you are seeing and post it back here ?

Virtualbox is in the default Multiverse repositories.

So as long as the Multiverse repository is enabled in your sources.list it will be listed in synaptic as available to install whether or not you want it.

---

### Post by ian-weisser on 2017-05-02
> **rosswmcgee said:**
> The fact that it's still listed in synaptic. And that there is no option to remove it only to install it.

That seems like expected behavior of software that has been removed.
All packages from all your sources should be 'listed', whether or not they are installed.

---

### Post by rosswmcgee on 2017-05-02
OK I will just leave things alone, sounds like the prudent thing to do. Thanks for the help.

---

### Post by russkyca on 2017-05-02
There's also two 'kinds' of virtualbox.... the one in the repos and the one you install from the actual website.  One is open source and provided by the repo and the one you install from the Virtualbox website.  I uisually install from the website.

---

### Post by rosswmcgee on 2017-05-03
That is where I installed it from,so and I guess that is what I removed, leaving the rep virtual box in synaptic intact though not installed . 

For me there are so many tools or apps available than what I have use for. Same goes for smartphones, they can do more than my needs. 

Thanks for the help.

---

### Post by howefield on 2017-05-04
> **rosswmcgee said:**
> That is where I installed it from,so and I guess that is what I removed, leaving the rep virtual box in synaptic intact though not installed . 

If you added the Virtualbox repository to your sources it can be removed or disabled easily enough by editing the /etc/apt/sources.list file but it won't do any harm left in place.

---

### Post by rosswmcgee on 2017-05-04
It has not been added to the sources list. Thanks for the comment.

---

