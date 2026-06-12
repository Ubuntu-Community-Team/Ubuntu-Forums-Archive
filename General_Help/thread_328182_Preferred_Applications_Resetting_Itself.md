---
title: "Preferred Applications Resetting Itself"
date: 2006-12-30
forum: General Help
---

### Post by _simon_ on 2006-12-30
My preferred applications for Web browser keeps resetting itself to custom.

Is there a text file I can edit?

---

### Post by bruenig on 2006-12-30
Generally speaking, I have found that it uses your alternatives more than the preferred applications list.

```
sudo update-alternatives --set x-www-browser /usr/bin/firefox
```

That is how you would set the alternatives to give firefox for the browser, but if you had another browser you wanted, like opera, you could just change /usr/bin/firefox to /usr/bin/opera in the command or whatever the path is to your browser.

Not sure if that will change the graphical preferred applications stuff, but I think it serves the same purpose that you are trying to achieve with preferred applications. At least I hope.

---

