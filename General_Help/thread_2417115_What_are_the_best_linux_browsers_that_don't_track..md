---
title: "What are the best linux browsers that don't track."
date: 2019-04-20
forum: General Help
---

### Post by jam7755 on 2019-04-20
Hi, for my job I enter data into a web based application.  The one hitch with this application is that it does not do well when you have multiple tabs open to see different parts of the application.  I spoke to customer support and the recommendation was to use another browser to log into the application a second time to view a different screen, and they recommended Chrome.  I am not a big fan of Chrome as it seems to track the living daylights out of a user.  I have been reading articles on the best browsers for Linux but when you look at the pros and cons some of them use old code or is using code from a source that is not trustworthy.  I am looking for a browser that will not track everything I do and is stable and reliable.  What browsers do you use in Linux, other than Firefox, that fits this bill?

---

### Post by &amp;KyT$0P# on 2019-04-20
What browser are you using now?

> **jam7755 said:**
> I spoke to customer support and the recommendation was to use another browser to log into the application a second time to view a different screen, 

You could also achieve this by running multiple instances of your current choice of browser using firejail sandboxing.

1) Install firejail if you don't already have it -
```
sudo apt-get install firejail xserver-xephyr
```
(Forcing one of the recommends to xserver-xephyr pulls in much fewer dependencies than the default selection.)


2) completely quit your browser


3) start your browser with a command like this -
```
firejail --overlay-tmpfs [COLOR="#FF0000"]<whatever browser you're using>[/COLOR]
```
If your browser is Firefox (or other Gecko-based or Goanna-based browser), you need to run the browser with [FONT=Courier New]-no-remote[/FONT] option and your command would be -
```
firejail --overlay-tmpfs firefox -no-remote
```

I gather you're not using Chromium, but if you are using a Chromium-based browser, you may need to run the browser with [FONT=Courier New]--no-sandbox[/FONT] option -
```
firejail --overlay-tmpfs chromium-browser --no-sandbox
```

It's possible you may need to customise firejail's sandbox profile for your browser.  Or if you don't know how and don't have time to figure it out at the moment, you can add [FONT=Courier New]--noprofile[/FONT] switch to firejail - so for example, if your browser is Firefox that you downloaded direct from Mozilla and extracted in your home directory, your firejail command would become -
```
firejail --noprofile --overlay-tmpfs ~/firefox/firefox -no-remote
```


4) Run again the command you ran in (3).  You should be able to do it while you still have the browser instance from (3) still running, and it should spawn a new browser instance.

And I wouldn't launch the browser any other way while you have these sandboxed instance(s) running.

---

### Post by Frogs Hair on 2019-04-20
Chrome is based on [Chromium]("https://www.chromium.org/Home") along with Vivaldi, Opera , Yandex, Iron, and many more lesser known browsers. They share many of the same settings , but aren't as heavily tied to google except for extensions and Google  search which can be changed.

Opera has its own extensions page, but can be made compatible  with the Chrome Web Store with an extension. Yandex is a Russian version of Chrome and Vivaldi is for power users. All these browsers have their own features not found in Chrome.  Iron does not track downloads of the browser or installations , but this means no update notifications and updating manually. I think all the user can do is choose a browser with less ties to Google and its services.

---

### Post by Rubi1200 on 2019-04-20
If you do not want to be tracked then you should not be using Chrome, period.

I do not think there is a complete solution to this problem, unless you disconnect from the internet.

However, I ran a test using this site: [https://panopticlick.eff.org/](https://panopticlick.eff.org/)

Run it with your current setup and I think you will find the results to be as shocking as mine were.

Then I tried two things:

Chrome with NoScript and Privacy Badger

Firefox with NoScript and Privacy Badger

(both addons are available)

The results were clearly in favour of Firefox, which leaked almost half the amount less data than Chrome.

I have not tested this combination with other browsers and it might be interesting to do so as a comparison.

Not sure what else to suggest.

---

### Post by VMC on 2019-04-21
> **Rubi1200 said:**
> If you do not want to be tracked then you should not be using Chrome, period.

I do not think there is a complete solution to this problem, unless you disconnect from the internet.

However, I ran a test using this site: [https://panopticlick.eff.org/](https://panopticlick.eff.org/)

Run it with your current setup and I think you will find the results to be as shocking as mine were.

Then I tried two things:

Chrome with NoScript and Privacy Badger

Firefox with NoScript and Privacy Badger

(both addons are available)

The results were clearly in favour of Firefox, which leaked almost half the amount less data than Chrome.

I have not tested this combination with other browsers and it might be interesting to do so as a comparison.

Not sure what else to suggest.^<== What he said! I don't care anymore. I don't give it much thought. My neighbors track me more than Google.

---

