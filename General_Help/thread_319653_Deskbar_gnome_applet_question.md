---
title: "Deskbar gnome applet question"
date: 2006-12-16
forum: General Help
---

### Post by alan_daniel on 2006-12-16
I'm using Edgy and I just ran across the Deskbar applet for the Gnome panel. I love that thing, but I'm having trouble getting it to work with a google search. I know it gives you a little how-to, but I have followed the how-to and the place it sends you to at Google doesn't exist anymore. In order to get an API from google, you have to have a website on which to use it. Since it's for desktop use, I don't know what to do. Anyone know how to get this to work, or am I just missing something (which is equally likely)

Thanks for any help

---

### Post by benmoreassynt on 2006-12-16
I'd appreciate an answer to this too

---

### Post by fragos on 2006-12-16
Perhaps if we knew what you typed and which command Deskbar provided did you run.  Then of course what happened.

---

### Post by alan_daniel on 2006-12-17
A command wasn't necessary to see this problem. The problem is that a google search can't even be a search option because you can't get an API from google anymore. If a command was necessary for an answer, I would have posted what happened. But this is a pre-command, configuration question.

---

### Post by ma7hatter on 2006-12-19
I also would appreciate an answer to this question.  It seems that the old instructions for getting google to work with the deskbar are deprecated because google has moved to an AJAX type API for searches.  Any knowladgable help would be greatly appreciated.

---

### Post by alan_daniel on 2006-12-20
Here's a slashdot posting about this:

[http://developers.slashdot.org/article.pl?sid=06/12/20/0155238](http://developers.slashdot.org/article.pl?sid=06/12/20/0155238)

I know this isn't an answer, just more information for anyone looking for it

---

### Post by `GooZ´ on 2007-01-06
Please someone give us an answer to this. I just LOVE the deskbar applet, and no google search functionality is really a showstopper. I would even be happy with only some kind of 'link' that opens google search results in my browser.

---

### Post by sloggerkhan on 2007-01-06
I am curious about this also.

---

### Post by fragos on 2007-01-06
I can see where linking the deskbar to google search would be convienient.  I don't however understand terms like "showstopper" associated with it.  The results would have to come up in a browser window anyway so I don't see the issue with using the browser search entry there.   This also makes focused search engines like Google Linux and Maps readily available

---

### Post by alan_daniel on 2007-01-06
Again, it's not so much that it's a pain to open the browser, it's just something that I and obviously others want working. It's a nice tool to have and can be very quick and handy.

---

### Post by ozp on 2007-01-07
I want to add many websearches, link its displayed here:
[http://www.gnome.org/~davyd/gnome-2-14/images/deskbar.png](http://www.gnome.org/~davyd/gnome-2-14/images/deskbar.png)

why they advertise the tool with many features and when you download it does not have the features advertised?

I tried to search for deskbar extensions plugins addons....

---

### Post by fragos on 2007-01-07
I t appears that the reason the Google API has disapeared is that it's being replaced by an AJAX API.

---

### Post by rioghal on 2007-01-07
My question is, what exactly does that search option do that you can't do with the deskbar applet otherwise? I use the deskbar applet daily and I don't have the google wsdl file or a google key. But, when I type something into the deskbar applet, it gives me the option of searching google for my search word(s). I did it and it works, but I don't have a google key or the google wsdl file. See the screenshot below. So, I'm wondering how this 'special key/file' is better than the normal Google search option that was with the deskbar applet in my Ubuntu 6.06.1 LTS system.. I haven't installed anything else outside of the Ubuntu repos and definitely not anything from Google.

---

### Post by sloggerkhan on 2007-01-07
Mine does not behave as your does. It will not search google from the deskbar.

---

### Post by fragos on 2007-01-07
Doesn't work on mine either.  Like sloggerkhan, I'm running 6.10 Edgy.  Google no longer supports downloading the API but they haven't disabled the API's use.

---

### Post by rioghal on 2007-01-07
I'm running Dapper (6.06.1 LTS) so I am guessing it's something that was in Dapper but taken out before Edgy released. Glad I stuck with Dapper, hehe

---

### Post by ozp on 2007-01-08
I dont mind google
what about torrents, imdb, wikipedia and many other searches?

how to enable them?

---

### Post by fragos on 2007-01-08
Here's the home page for the deskbar applet [http://raphael.slinckx.net/deskbar/](http://raphael.slinckx.net/deskbar/).  You can learn a lot about deskbar there.  Perhaps you may wish to get envolved with the project.

---

### Post by `GooZ´ on 2007-01-08
> **ozp said:**
> I dont mind google
what about torrents, imdb, wikipedia and many other searches?

how to enable them?

You can search them by just enabling the option 'browser search'.

---

### Post by sloggerkhan on 2007-01-09
my comp seems not to show those when enabled either.

---

### Post by ozp on 2007-01-16
> **`GooZ´ said:**
> You can search them by just enabling the option 'browser search'.

I did not found this option

---

### Post by gtr225 on 2007-04-12
Me neither

---

### Post by ozp on 2007-04-12
well so much for the deskbar...

when I try to search I can only search ubuntu stuff

is it so hard to make it search google?

---

### Post by gtr225 on 2007-04-12
I found a fix. Unzip the attached archive and place the file "google.src" in /usr/share/firefox/searchplugins and google search should work. It appears the issue is deskbar in edgy doesn't support firefox 2.0 search plugins, but rather version 1.5 plugins. I'm assuming this file is a firefox 1.5 search plugin because it works.

---

