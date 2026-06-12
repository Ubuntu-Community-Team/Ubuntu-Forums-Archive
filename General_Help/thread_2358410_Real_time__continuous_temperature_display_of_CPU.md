---
title: "Real time / continuous temperature display of CPU"
date: 2017-04-13
forum: General Help
---

### Post by foomate on 2017-04-13
I am using lm-sensors, but it can show the temps only for the moment I type "sensors". Is there a real-time temperature display software?

Thanks

---

### Post by howefield on 2017-04-13
How about..

```
watch sensors
```

That will update the information output from sensors.

---

### Post by foomate on 2017-04-13
Yes! Thank you :KS

---

### Post by howefield on 2017-04-13
> **foomate said:**
> Yes! Thank you :KS

Cool, you're welcome.

There are other applications that will do what you want but when you already have lm-sensors installed the above is as good as any :)

---

### Post by vasa1 on 2017-04-13
I used this a long time ago:```
indicator-multiload/xenial 0.4-0ubuntu4 amd64
  Graphical system load indicator for CPU, ram, etc.
```Now, I use conky.

---

### Post by foomate on 2017-04-13
Thanks guys :KS And beside conky, anything else? (because howfield said applications as in plural and I want to know as much as possible :p)

---

### Post by dragonfly41 on 2017-04-13
> [COLOR=#000000]And beside conky, anything else? 
[/COLOR]I've installed gkrellm which has a number of plugins.
If you have Synaptic Package Manager search "gkrell"

I've installed ..
gkrellm
gkrellm-cpufreq
gkrellm-hdplop
gkrelltop


and if you want the server version .. 
e.g. for a remote server or to stream back logs ..

gkrellmd
gkrelltopd

---

### Post by vasa1 on 2017-04-13
> **foomate said:**
> ... anything else? (because howfield said applications as in plural and I want to know as much as possible :p)
Well, you can search the internet using terms such as cpu, temp, monitor, indicator, linux and so on. Who knows, you may find something no one mentions here.

---

### Post by &amp;KyT$0P# on 2017-04-13
> **foomate said:**
> Thanks guys :KS And beside conky, anything else? (because howfield said applications as in plural and I want to know as much as possible :p)
I use Psensor.  It's available in the standard repositories.

---

### Post by vasa1 on 2017-04-14
> **halogen2 said:**
> I use Psensor.  It's available in the standard repositories.
+1

Here's an old thread of mine which I totally forgot about: [https://ubuntuforums.org/showthread.php?t=1998005&highlight=psensor](https://ubuntuforums.org/showthread.php?t=1998005&highlight=psensor)

---

### Post by howefield on 2017-04-14
> **foomate said:**
> (because howfield said applications as in plural and I want to know as much as possible :p)

Well I have an alias in .bashrc to start watch sensors as it seems to work as well as anything else and provide plenty information but in the past have also used xsensors which is a small application with a gui and updates output in real time.

[ATTACH=CONFIG]274542[/ATTACH]

I've also used the excellent psensors mentioned above.

---

