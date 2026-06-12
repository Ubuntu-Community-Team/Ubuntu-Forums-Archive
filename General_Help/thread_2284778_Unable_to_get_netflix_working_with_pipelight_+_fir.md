---
title: "Unable to get netflix working with pipelight + firefox"
date: 2015-07-01
forum: General Help
---

### Post by carl24 on 2015-07-01
Hi,
When I updated to 14.04 netflix-desktop stopped working. I tried using pipelight but I'm having an issue getting it to work. I followed instructions from [http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

```

sudo apt-add-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update
sudo pipelight-plugin --enable silverlight

```
[http://fds-team.de/pipelight/](http://fds-team.de/pipelight/) "Silverlight5.1" shows my user agent switcher is working, but the rest of the tests fail. about: plugins in firefox 38 does not show the silverlight plugin.

I tried the closing firefox & running the following:

```

rm -rf ~/.wine-pipelight/
sudo pipelight-plugin --enable silverlight

```

& also tried 
```

sudo pipelight-plugin --create-mozilla-plugins

``` but neither resolved the issue.

```

pipelight-plugin --system-check

```

The system check shows the only issue is "libnetapi.so" is missing, but the pipelight FAQ says that's not required.

---

### Post by carl24 on 2015-07-01
Well could have skipped all of that, netflix works out of the box in google chrome (note: not chromium). Leaving this up in case anyone tries the same thing, just use chrome instead for now for netflix.

---

### Post by sammiev on 2015-07-01
> **carl24 said:**
> Well could have skipped all of that, netflix works out of the box in google chrome (note: not chromium). Leaving this up in case anyone tries the same thing, just use chrome instead for now for netflix.

Hi carl,

I use google chrome for netflix with no issues. Glad you have it working.

Please use Thread Tools from above your 1st post and mark this thread as solved to help others. :)

---

### Post by SeijiSensei on 2015-07-02
To use pipelight with Netflix you need to use a Firefox add-on to spoof your browser's User-Agent string.  Did you do that?

---

### Post by carl24 on 2015-07-02
Thanks SeijiSensei. I did have a user agent switcher & verified that was working, but the pipelight plugin wasn't registering with firefox for some reason. I'm marking it as solved as sammiev mentioned with using google chrome as a workaround.

---

### Post by awunes on 2015-07-08
> **sammiev said:**
> Hi carl,

I use google chrome for netflix with no issues. Glad you have it working.

Please use Thread Tools from above your 1st post and mark this thread as solved to help others. :)

but this isn't solved it's worked around!!! there is a difference.

How would one get it working in Firefox? ...

Well I found that manually installing Firefox 39 got it to work - pipelight was seen and silverlight was prompted to activate and it succeeded.. NOW it is Solved!!! though i should mention I'm on Linux Mint 17 and not Ubuntu - but the two are so similar I suspect it'd work on Ubuntu as well. Good Luck all :)

---

### Post by QIII on 2015-07-08
Not without pipelight.

---

### Post by monkeybrain20122 on 2015-07-09
> **carl24 said:**
> Thanks SeijiSensei. I did have a user agent switcher & verified that was working, but the pipelight plugin wasn't registering with firefox for some reason. I'm marking it as solved as sammiev mentioned with using google chrome as a workaround.

To register it with FF close FF and run in terminal

```
sudo pipelight-plugin --create-mozilla-plugins
```

---

### Post by Ryback on 2015-10-08
> **monkeybrain20122 said:**
> To register it with FF close FF and run in terminal

```
sudo pipelight-plugin --create-mozilla-plugins
```

Thank you monkey brain that fixed my problem with firefox.

---

### Post by jdkcarlson on 2016-04-06
I did all the Pipelight installation and created the plugins, installed a User Agent Switcher add-on for Firefox, and switched the user agent to Internet Explorer 8. Netflix still redirects me to system requirements. What can I do?

---

### Post by QIII on 2016-04-06
jdkcarlson -

Tagging on to an old thread marked solved is not the best way to get your question answered.

Please start a new thread describing your unique situation.

Feel free to refer to this thread in your new one.

Closed.

---

