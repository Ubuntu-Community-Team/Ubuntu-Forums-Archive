---
title: "Java!"
date: 2017-12-09
forum: General Help
---

### Post by dutchman5172 on 2017-12-09
I'm new to Ubuntu, still not very familiar with the commands/structure. Just switched over because I ran out of patience with Windows.

Everything is working great, however I have a website I need to access frequently for work that requires Java,

The new firefox and chrome do not support Java to my knowledge. I don't mind having to use a different brower for just that website if need be.

So how do I get a Java enabled browser on Ubuntu? Is Wine and internet explorer the only option or is there something simpler?



Thanks!

---

### Post by &amp;KyT$0P# on 2017-12-09
You could download an older Firefox version from [here]("https://ftp.mozilla.org/pub/firefox/releases/") and run it with a separate Firefox profile.

1) Start the older Firefox [Profile Manager]("http://kb.mozillazine.org/Profile_Manager")

2) Create a new Firefox profile.  Give it a unique name, **leave the default folder location**, and click Finish.

3) Exit the Profile Manager

4) Start your normal version of Firefox with the Profile Manager.  Select your normal profile, select "Don't ask at startup", and click "Start Firefox".

5) Now, when you want to run the older Firefox, run it like this -
```
/path/to/older/firefox -no-remote -P <profilename>
```
replacing <profilename> with the name you gave your new profile in step 2.  The [FONT=Courier New]-no-remote[/FONT] option is so that you can run your normal Firefox at the same time.


Does this help?

---

### Post by Yellow Pasque on 2017-12-09
You can look at Pale Moon browser. [https://www.palemoon.org/](https://www.palemoon.org/)
Also, you should realize that there's a reason FF and Chrome moved away from plugins like Java (security). Consider something like firejail if appropriate.

---

### Post by dutchman5172 on 2017-12-09
> **halogen2 said:**
> You could download an older Firefox version from [here]("https://ftp.mozilla.org/pub/firefox/releases/") and run it with a separate Firefox profile.

1) Start the older Firefox [Profile Manager]("http://kb.mozillazine.org/Profile_Manager")

2) Create a new Firefox profile.  Give it a unique name, **leave the default folder location**, and click Finish.

3) Exit the Profile Manager

4) Start your normal version of Firefox with the Profile Manager.  Select your normal profile, select "Don't ask at startup", and click "Start Firefox".

5) Now, when you want to run the older Firefox, run it like this -
```
/path/to/older/firefox -no-remote -P <profilename>
```
replacing <profilename> with the name you gave your new profile in step 2.  The [FONT=Courier New]-no-remote[/FONT] option is so that you can run your normal Firefox at the same time.


Does this help?

Okay, steps 1-3 are done. I went with Firefox 26, figured that'd be old enough to be able to use Java.

As for starting the originally installed Firefox with profile manager, what is the directory of the original Firefox file? I tried searching for it but don't come up with a usable location.

Thanks.

---

### Post by dutchman5172 on 2017-12-09
> **Temüjin said:**
> You can look at Pale Moon browser. [https://www.palemoon.org/](https://www.palemoon.org/)
Also, you should realize that there's a reason FF and Chrome moved away from plugins like Java (security). Consider something like firejail if appropriate.

Yea, the only thing I would be using this browser for is the work website that require it.

I did just download Pale Moon, seems to work okay but it still comes up as having java disables, and I don't see an option in the preferences to enable it. How do I go about doing that?

EDIT: I downloaded a java plug in and enabled it, however the website is still telling me java is disabled and the content won't work properly.

---

### Post by &amp;KyT$0P# on 2017-12-09
> **dutchman5172 said:**
> As for starting the originally installed Firefox with profile manager, what is the directory of the original Firefox file? 
If you don't know, you probably have the standard Ubuntu package version.  In which case, you can simply run
```
firefox -ProfileManager
```

---

### Post by dutchman5172 on 2017-12-09
> **halogen2 said:**
> If you don't know, you probably have the standard Ubuntu package version.  In which case, you can simply run
```
firefox -ProfileManager
```

That did it, thanks!

---

