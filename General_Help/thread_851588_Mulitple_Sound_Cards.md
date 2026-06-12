---
title: "Mulitple Sound Cards"
date: 2008-07-06
forum: General Help
---

### Post by Esahp on 2008-07-06
I have of course on board sound, and a regular sound card.

Yesterday I did something to get the actual sound card working (I forgot what), but after I restarted for something completely unrelated it has switched back to the on board sound.

How would I change it back, and make it stay that way?

Thanks.

---

### Post by Esahp on 2008-07-06
Sorry if this is too early a bump, but I know how quickly threads get pushed off the screen. Any ideas?

---

### Post by iaculallad on 2008-07-06
> **Esahp said:**
> I have of course on board sound, and a regular sound card.

Yesterday I did something to get the actual sound card working (I forgot what), but after I restarted for something completely unrelated it has switched back to the on board sound.

How would I change it back, and make it stay that way?

Thanks.

Post the output of the terminal command below:

```
asoundconf list
```

---

### Post by Esahp on 2008-07-06
```

phase@geek:~$ asoundconf list
Names of available sound cards:
CMI8738
ICH5
phase@geek:~$ 

```

CMI8738 is the one I need I do believe.

---

### Post by iaculallad on 2008-07-06
> **Esahp said:**
> ```

phase@geek:~$ asoundconf list
Names of available sound cards:
CMI8738
ICH5
phase@geek:~$ 

```

CMI8738 is the one I need I do believe.


```
sudo asoundconf set-default-card CMI8738
```

That should do it.

---

### Post by Esahp on 2008-07-07
That didn't work. I also tried /etc/init.d/alsa-utils restart after it, as well as the same for the other one listed. I still hear the sound through the on-board device.

The weird thing is, when I ran alsa-utils restart, the speakers that I *want* to work made a little noise.

---

### Post by Esahp on 2008-07-07
Right, nevermind. Programs are defaulting to using pulse instead of alsa (alsa works after I change it in the Audio options), how would I make it the default card in pulse too?

---

### Post by cariboo on 2008-07-07
You can go into your BIOS and turn off your on board sound card.

Jim

---

