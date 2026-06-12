---
title: "Does Ubuntu support GD functionality in PHP?"
date: 2007-06-10
forum: General Help
---

### Post by noom on 2007-06-10
Installed Ubuntu yesterday and I love it. (Could be a bit faster in processing but love everthing else about it)

Anyway, the problem is, when ever i run my php scripts that create a png image (a captcha image) using the GD functionality in PHP, (I run these live from the internet, by the way on [http://)](http://)). An error comes up:-

The image &#8220;[http://www.showproperty.co.uk/agents/signup/index.php](http://www.showproperty.co.uk/agents/signup/index.php)" cannot be displayed, because it contains errors.

I tried both FireFox and Epiphany, yet It works fine with Windows and Internet Explorer.

Please Help

Thanks

---

### Post by conjur3r on 2007-06-10
Yes ubuntu does support the GD libraries.  You got to install it though:
# sudo apt-get install php5-gd

Then restart apache.

The problem may also be in your php code.  [http://www.showproperty.co.uk/agents/signup/index.php](http://www.showproperty.co.uk/agents/signup/index.php) outputs in HTML but is identified as a PNG image.  You may have your header declaration outputting incorrectly?

---

### Post by noom on 2007-06-10
I dont understand, i mean It works in IE,

also my header is [PHP]Header("Content-Type: image/png");[/PHP]

its a captcha image, what the script does, it creates a random number, and outputs that number in an image format (png) then through HTML, i source that new PNG image like so[HTML]<img src='verify.png'>[/HTML]

I dont undertstand what can be so different to Windows and Ubuntu within this case?

The rest of my scripts work fine, its only the ones that have the captcha images that dont work.

and there all being run on my hosting server which as i said doesnt have a problem becuase they work on windows.

please help

thanks


[COLOR="Red"]EDIT:-

I just removed the HTML code that outputs the verify.png image, and the problem still occurs???[/COLOR]

---

### Post by noom on 2007-06-10
OH Crap i Understood your reply, that the header was making the whole document a PNG image. I removed it and it works, thanks alot man.

still tho my lesson learnt is that ubuntu is stricter in reading things, tbh that is probably a good thing especially for web developers.

THANKS.

---

### Post by noom on 2007-06-10
thanks

---

### Post by conjur3r on 2007-06-10
It was probably the browser.  IE well... is IE and there are many things it does that doesn't make sense.  Next time something like this happens, add a test using firefox on windows to isolate the OS as a possibility.

---

