---
title: "Java"
date: 2004-11-28
forum: General Help
---

### Post by jayclark on 2004-11-28
Has anyone been able to get java working? So I could use lets say Limewire. Its easy to get the java plugin to work for Firefox but has anyone got it to work to run software that relies on it? I know its not easy on Debian but some way some has. I tried blackdown java to no success.

---

### Post by scp on 2004-11-28
I have it working with no issues. I am using j2sdk1.4.2_06. I have heard of people having some issues with 1.5, but I have not tried it. 

My procedure was pretty much installing it in /usr/local, linking /usr/local/java and /usr/java to /usr/local/j2sdk1.4.2_06 and putting /usr/java/bin in my $PATH.

To install the plugin I just linked ~/.mozilla/plugins/libjavaplugin_oji.so to /usr/java/jre/plugin/i386/ns610-gcc32/libjavaplugin_oji.so .

I am running things fine in Firefox and I am using Azureus and Furthur without a problem. 

What errors are you seeing?

---

### Post by jayclark on 2004-11-28
I have messed up my Ubuntu install and lost the cd and my cd burner went bad so I'm waiting on the cds to ship here. So I can't remember exactly what it said but something about java not being in its path. I guess it means it can't find where java was installed.

---

### Post by scp on 2004-11-28
Take a look at this. This isn't the procedure I used, but this may help you out.

[http://kitech.com.my/ubuntu/4.10/index.html#jre](http://kitech.com.my/ubuntu/4.10/index.html#jre)

---

### Post by jayclark on 2004-11-28
I'll give it a try once my cds get here, which I hope is this week.

---

### Post by jdodson on 2004-11-29
if you ordered your cds in the last month or so it might take sometime for them to ship to you(because of the high demand).  if you have a friend that could download and burn it for you, that would speed things up quite a bit.

---

### Post by jayclark on 2004-11-29
I order them in September.

---

### Post by jayclark on 2004-11-29
I just checked the mail and I got them.

---

### Post by kickinmhl on 2005-05-04
I am having a problem getting Java installed as well.
Actually the process listed in the link about is what I used and it still doesn't work.

I did check the $PATH though and I don't see java in there.

Can you tell me how to edit the $PATH?

Thanks!

---

