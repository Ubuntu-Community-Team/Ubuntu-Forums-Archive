---
title: "How to install FreeTube?"
date: 2021-07-02
forum: General Help
---

### Post by sixmalo on 2021-07-02
I can't install FreeTube. I don't know what to do.

Ubuntu 20.04.2 LTS
[https://user-images.githubusercontent.com/86832896/124266062-c3862f00-db36-11eb-9842-3f42c0c6ee4f.png](https://user-images.githubusercontent.com/86832896/124266062-c3862f00-db36-11eb-9842-3f42c0c6ee4f.png)
Help me please :,(

---

### Post by coffeecat on 2021-07-02
Not a tutorial. *Thread moved to **General Help** sub-forum.*

---

### Post by mikewhatever on 2021-07-02
What is FreeTube? Is the image above related, or is it irrelevant?

...apparently, deb64 packages are anailable at [https://freetubeapp.io/#download](https://freetubeapp.io/#download).

Should be just download and install, if all works as expected.

---

### Post by sixmalo on 2021-07-02
private youtube client.

++++++++++++++++++++++++++++++++

Is work! Im sorry. I dont know what is going on...

I tryied all day.

[https://user-images.githubusercontent.com/86832896/124319024-da01aa00-db79-11eb-87fd-f3d335996524.png](https://user-images.githubusercontent.com/86832896/124319024-da01aa00-db79-11eb-87fd-f3d335996524.png)

---

### Post by TheFu on 2021-07-02
There's a flatpak for freetube.  The github project page has links. [https://github.com/FreeTubeApp/FreeTube](https://github.com/FreeTubeApp/FreeTube)  Looks like a node.js desktop app to me.

Also, the license is AGPL on github, so whatever those huge images above are showing are showing a bogus license.  I'm not sure I believe the marketing in the "features" list, especially the claims about tracking and privacy.  Google isn't dumb.  If we access any of their content located on their servers, they are tracking us. Period.

Would be nice of the images were thumb-nailed for low bandwidth people.

---

### Post by coffeecat on 2021-07-03
@sixmalo, I've reduced your huge images to links. If you wish to include images in posts, please use the forum attachment function - the paperclip icon in the message toolbar. That way you get clickable thumbnails.

---

### Post by mIk3_08 on 2021-07-03
You can download Freetube .deb package, just click [here]("https://freetubeapp.io/#download"). And you can follow some installation instruction here if you want. just click [here]("https://www.ubuntubuzz.com/2020/10/run-freetube-portable-on-ubuntu.html"). But you can run the .deb package directly to you Ubuntu using the Gdebi Package. Good Luck.

---

### Post by Frogs Hair on 2021-07-03
Currently running the program from the app image on 21.04. The app image needs to be set as executable in properties/permissions by right clicking the package.

---

### Post by dddman on 2021-07-03
I have Adblock for youtube; AVG antitrack for the internet and VPN for privacy.  I don't see Freetube adding anything to this.

---

### Post by TheFu on 2021-07-03
>  I have Adblock for youtube; AVG antitrack for the internet and VPN for privacy. I don't see Freetube adding anything to this. 

Adblock and AVG have been caught selling data.
[LIST]
[*][https://www.wired.com/2016/03/heres-how-that-adblocker-youre-using-makes-money/](https://www.wired.com/2016/03/heres-how-that-adblocker-youre-using-makes-money/)
[*][https://www.tomsguide.com/news/avast-avg-data-collection](https://www.tomsguide.com/news/avast-avg-data-collection)
[/LIST]

Your browser is keeping all sorts of data, so the only way to protect ourselves from our browsers is by starting with a 100% clean browser install when we don't want to be tracked. This is a never-used-before setup. Never trust "incognito modes."  Every browser that attempts to provide incognito browsing has failed. Multiple. Times.  For example:
[https://arstechnica.com/gadgets/2021/03/judge-rules-5-billion-google-chrome-incognito-mode-lawsuit-can-go-forward/](https://arstechnica.com/gadgets/2021/03/judge-rules-5-billion-google-chrome-incognito-mode-lawsuit-can-go-forward/)

That means we either need to use an in-memory-only file system overlay (firejail does this) or start with a fresh userid each time we want privacy, then remove the userid and all files when we are done browsing. Not hard to script, but putting in all the addons we all like is a hassle.

Not sure how any of the tools can provide the subscription feature from FreeTube.  If we use our google/YT logins, then we've given up all privacy.  Freetube claims to keep subscription details local and has hooks for both TOR and a proxy server.  I'm guessing that someone has access to that proxy data, but it isn't google.  A VPN without all the other aspects to reset browser config, not transmit tracking cookies, fudge battery power drain, screen size, and all the other data used by "super trackers" and we didn't actually achieve the desired privacy.  The EFF created a tool to give us an idea about how unique our browser is.  [https://coveryourtracks.eff.org/](https://coveryourtracks.eff.org/)  Lots of information there.  Using 2 different browers, but running inside firejails, my results were:
> Your browser fingerprint appears to be _unique among the 254,031_ tested in the past 45 days.

Whether any of the added privacy claims by FT are true is yet to be proven.  I'm not thrilled with JS-based applications, but that's a personal bias.

There are no absolutes and each person has to determine what "good enough" privacy means to us.

---

### Post by dddman on 2021-07-04
Adblock/ AVG it doesn't stop there.  Every time you tick the "I Agree" you just sign up for more info mining.  Can't be helped, info mining is here to stay.

I bet Freetube comes with a agreement.

Hey TheFu, nice post :)

---

### Post by dragonfly41 on 2021-07-04
Experimenting with that browser fingerprint tracking test I see that Brave browser
returns ..

[TABLE="class: tracker_results"]
[TR]
[TD="class: test_label"]Protecting you from [fingerprinting]("https://coveryourtracks.eff.org/results?&aat=1&dnt=1111&fpi_whorls=%7B%22v2%22%3A%7B%22plugins%22%3A%22Plugin+0%3A+Online+com.adobe.pdf+Viewer%3B+%3B+xYMmTpUKFChQoUKlSJECBAAgwYs27dOn%3B+%28%3B+application%2Fpdf%3B+pdf%29.+Plugin+1%3A+OpenSource+portable-document-format+plug-in%3B+Portable+Document+Format%3B+w48.++++fPHjRoUq1aNmTp0atWLFChw4%3B+%28Portable+Document+Format%3B+application%2Fx-google-chrome-pdf%3B+pdf%29.+Plugin+2%3A+TJEChw4%3B+3btWr16dOnzZMmz58.++fvXr16du379%3B+VqVq169.fPHDhQo%3B+%28OnzZMmzZs27duXLly5cOnTp069evXrVK%3B+%3B+%29.+Plugin+3%3A+gwYs27dO%3B+jx4cu379.fPnTJky5cOnTp06duXrVKlS%3B+58.fPHDBgQIEix48%3B+%28u3btWLFiRIky5cOnz5cOHjRo06du37du%3B+%3B+%29.+%22%2C%22hardware_concurrency%22%3A4%2C%22audio%22%3A%22123.2441517923944%22%2C%22canvas_hash_v2%22%3A%22b3ee71ec3ad38ced757aa377f4fce64a%22%2C%22webgl_hash_v2%22%3A%22853a6bbfd5ba4bae8f8428af0086bb15%22%7D%7D#fingerprintTable")?[/TD]
[TD="align: center"][COLOR=#5CB900]&#9685;[/COLOR] your browser has a randomized fingerprint[/TD]
[/TR]
[/TABLE]

And here is another vulnerability testing link to add to the pot.
[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)

[P.S.] Another wheeze to try is using one time disposable email addresses as browser extension.

[https://burnermail.io/](https://burnermail.io/)

---

### Post by Frogs Hair on 2021-07-04
Free Tube uses the GPLv3 license and has user controlled local only history storage.

---

