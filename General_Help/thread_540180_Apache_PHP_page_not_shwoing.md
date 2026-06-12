---
title: "Apache PHP page not shwoing"
date: 2007-09-01
forum: General Help
---

### Post by Yodude on 2007-09-01
I recently se up Apache to serve a page ( bandwidth monitor "cacti" ). I installed PHP and the apache PHP module, restarted Apache, but the page is still not showing, it's being treated as a file to download by firefox, can someone please help me ?

---

### Post by callan79 on 2007-09-01
> **Yodude said:**
> I recently se up Apache to serve a page ( bandwidth monitor "cacti" ). I installed PHP and the apache PHP module, restarted Apache, but the page is still not showing, it's being treated as a file to download by firefox, can someone please help me ?

Hi Yodude,

I'm no expert, but a colleague at work helped me to install Cacti. One thing we did was to isntall Apache2, as he said that Apache2 already has PHP support in there, but regular Apache needs to have it manually added.

Once Apache2 was installed, I had to do this every boot :

```
sudo /etc/init.d/apache stop
sudo /etc/init.d/apache2 start
```

And then Cacti worked OK.

I'm still learning how to make Apache2 start on boot, and make sure Apache does not start... any takers?

Cheers
Callan

---

