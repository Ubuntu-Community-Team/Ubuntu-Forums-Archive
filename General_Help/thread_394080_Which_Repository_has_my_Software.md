---
title: "Which Repository has my Software?"
date: 2007-03-26
forum: General Help
---

### Post by Tookelso on 2007-03-26
Hello,

I'd like to know how to find out which repository I'm retrieving a piece of software from.

For example, I have software "FOO", which a friend of mine is interested in.  It is not in the default repositories, so software "FOO" is not available on my friend's Synaptic.  How do I tell my friend which repository to add to their sources.list file?

This seems really simple and fundamental, but I can't find the answer anywhere.  I've searched the APT HOWTO [http://www.debian.org/doc/manuals/apt-howto/index.en.html](http://www.debian.org/doc/manuals/apt-howto/index.en.html) and it doesn't mention anything like this.

Is there some kind of command you can run to say:

apt-get whichrepo "FOO"

Thanks,

--Took

---

### Post by Ramses de Norre on 2007-03-26
apt-cache policy FOO

---

### Post by zvacet on 2007-03-26
Be sure that you haveall repositories open.If still can not find it in synaptic go to the FF search engine and under Ubuntu packages type name of program you are interested in.

---

### Post by Tookelso on 2007-03-26
> apt-cache policy foo

Thank you very much!  Here is what the output looked like.  Exactly what I wanted.

$ apt-cache policy kturtle
kturtle:
  Installed: 4:3.5.5-0ubuntu1
  Candidate: 4:3.5.5-0ubuntu1
  Version table:
 *** 4:3.5.5-0ubuntu1 0
        500 **[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages**
        100 /var/lib/dpkg/status

---

