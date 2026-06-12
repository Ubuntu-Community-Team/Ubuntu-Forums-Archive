---
title: "Does sudo lshw reveal any senstive information?"
date: 2017-03-23
forum: General Help
---

### Post by John_Patrick_Mason on 2017-03-23
I recently posted the results of sudo lshw in the forums without thinking while asking for support. I'm just wondering whether it contains any sensitive information that could be used to my detriment. I'm not familiar with the command, that's why I'm asking.

---

### Post by yetimon_64 on 2017-03-23
> **John_Patrick_Mason said:**
> I recently posted the results of sudo lshw in the forums without thinking while asking for support. I'm just wondering whether it contains any sensitive information that could be used to my detriment.

The output of lshw does often contain serial numbers and UUIDs and IP addresses etc that could possibly identify your specific hardware/installation. 
When you do run it use the "-sanitize" switch with it if you want more privacy orientated output from it.
From "man lshw" ...
> ```
       -sanitize
              Remove  potentially  sensitive  information  from output (IP addresses, serial numbers,
              etc.).
```

---

### Post by vasa1 on 2017-03-23
And, following yetimon_64's advice, you can go back to that other post and replace the old information there with the sanitized one by clicking the *Edit Post* button and taking things from there.

---

### Post by John_Patrick_Mason on 2017-03-23
The reason I also got kinda of worried is because my other computer that has Lubuntu installed on it, prompted me for my network password out of the blue. The prompt said something about how users weren't allowed to modify network settings or something similar.

---

