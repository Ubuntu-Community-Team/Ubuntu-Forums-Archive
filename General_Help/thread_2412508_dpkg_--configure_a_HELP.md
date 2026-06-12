---
title: "dpkg --configure a HELP"
date: 2019-02-13
forum: General Help
---

### Post by redsky27 on 2019-02-13
Hello
I will link photos so you can have a look, i'm not terrible sure how this all happened, MAYBE I have a virus? idk

anyway, thanks very much for the help, if you'd like more information i'd be more than happy to oblige

thanks again!!! 

[https://imgur.com/4C5o3xc](https://imgur.com/4C5o3xc)

---

### Post by Impavidus on 2019-02-14
Could you next time paste your terminal output in your post as text (using code tags, as I do below), not use a screenshot on some third-party site where I have to enable scripts and block 10 ads? That's easier for us.

I don't think there are any Linux viruses in the wild now, although other malware exists. But you most likely have simply a messed-up package manager. You have a dependency problem and, assuming you run Ubuntu 18.04, your gpg package is outdated.

What do you get from```
sudo apt update
sudo apt install -f
```

---

### Post by SeijiSensei on 2019-02-14
Just to make sure the command is

```
sudo dpkg --configure -a
```

Did you happen to leave off the hyphen in front of "a"?

---

