---
title: "Default Browser"
date: 2017-05-23
forum: General Help
---

### Post by Crimple on 2017-05-23
Hi.

I have [Palemoon]("https://en.wikipedia.org/wiki/Pale_Moon_%28web_browser%29") installed through its own [installer]("http://linux.palemoon.org/download/installer/#") and configured to be the default browser.
Some applications though still use FF to search online, like [Calibre]("https://en.wikipedia.org/wiki/Calibre_%28software%29") when I copy a segment of text.
Is there a way to force Calibre, or others, to use Palemoon ? And why don't they use it in the first place ?

Thanks.

---

### Post by vasa1 on 2017-05-23
> **Crimple said:**
> ...
Is there a way to force Calibre, or others, to use Palemoon ? And why don't they use it in the first place ?
...
Have you looked at Calibre's settings? Perhaps there's something in there? And why some applications don't use the "default browser" is what I'd like to know as well!

Please run```
update-alternatives --get-selections | grep -i browser
```and post the output here.

BTW, Dennis N had once mentioned galternatives, in the repos (universe), as a nice GUI for changing values in update-alternatives.

---

### Post by LastDino on 2017-05-23
Hi!
How have you set Palemoon as your default browser? 

There are 3 alternatives to do this, 
1) Through browser only (which asks to set itself as default)
2) But you also wan to by changing application settings>select "whatever application you want as default"
3) By updating alternatives (easy tut for that > [https://askubuntu.com/questions/805969/how-to-change-default-program-for-https-links-in-xubuntu-xfce/806126#806126](https://askubuntu.com/questions/805969/how-to-change-default-program-for-https-links-in-xubuntu-xfce/806126#806126) )

has non of this worked? 

Then there is 4th way, which is changing xdg settings

```

xdg-settings set default-web-browser google-chrome.desktop
```

something like that..

---

### Post by Crimple on 2017-05-23
> **LastDino said:**
> Hi!
How have you set Palemoon as your default browser? 

There are 3 alternatives to do this, 
1) Through browser only (which asks to set itself as default)
2) **But you also wan to by changing application settings**>select "whatever application you want as default"
3) By updating alternatives (easy tut for that > [https://askubuntu.com/questions/805969/how-to-change-default-program-for-https-links-in-xubuntu-xfce/806126#806126](https://askubuntu.com/questions/805969/how-to-change-default-program-for-https-links-in-xubuntu-xfce/806126#806126) )


Number 2 worked, and I should've gotten there on my own :redface:

@lastDino
@vasa1
many thanks

---

### Post by LastDino on 2017-05-23
you're welcome!

---

