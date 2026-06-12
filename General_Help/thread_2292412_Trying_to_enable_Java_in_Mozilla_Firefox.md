---
title: "Trying to enable Java in Mozilla Firefox"
date: 2015-08-27
forum: General Help
---

### Post by jakerz530 on 2015-08-27
So I don't know if this was posted or not. I saw several installing java posts and what not but I may have a different problem.

So I installed java fine. I'm pretty sure I did anyways. Whenever I use the 'java -version' command in terminal it comes up with 'java version "1.8.0_60"'

Now here is where I ran into a problem. I read the wikihow on how to enable java in mozilla. I had gone through that whole process of making a directory in /usr/lib/mozilla/plugins and creating a link so that it links the libnpjp2.so file.

I tried a java tester website and also java's verify website as well but no luck. So I tried it making the directory again, copy, etc. I triple checked everything I was typing. I tried and it said the same. "Java is not enabled in your browser."

So I decided to look into the java directory, and I found something interesting:

[ATTACH=CONFIG]264087[/ATTACH]

There is no libnpjp2.so file? So what would I need to do in order to enable java? I'm completely lost and I can't find out a solution. Thank you in advance for your help.

---

### Post by Yellow Pasque on 2015-08-27
[http://ubuntuforums.org/showthread.php?t=2196114&p=12884825#post12884825](http://ubuntuforums.org/showthread.php?t=2196114&p=12884825#post12884825)

---

### Post by QIII on 2015-08-27
Why not just do it the[ easy way]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"), so Oracle Java is updated when you do your normal Ubuntu updates?

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

The script does all the work for you.

And please don't cut and paste large images.  Some users have slow connections and others have data limitations.

Use the attachment functionality orovided by the paperclip button in the tool bar above the text entry box to give others the choice of whether or not to biew the image.

---

