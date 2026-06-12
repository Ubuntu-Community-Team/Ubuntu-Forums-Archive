---
title: "How to tell if you have a 32-bit or 64-bit machine?"
date: 2017-02-27
forum: General Help
---

### Post by John_Patrick_Mason on 2017-02-27
Hi everyone,

I was reading through the following [https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)  thread since I've been considering for quite a while switching from Ubuntu to a lighter distribution such as Lubuntu on one of my old PCs, when I encountered the following command:

```
sudo lshw -C cpu | grep -i width
```

As you know the command above is supposed to tell whether you have a 32- or 64-bit processor. Well, the output of the command showed that I had a 64-bit processor, which really surprised me since I've been running the 32-bit version of Ubuntu forever.

My question goes like this: 
Is it possible that there might have been a mistake, that even though the output of the command indicated my machine supports 64-bit, that I might still actually have a 32-bit machine?

---

### Post by howefield on 2017-02-27
What does the following output..

```
lscpu | grep "CPU op-mode(s)"
```

---

### Post by John_Patrick_Mason on 2017-02-27
> **howefield said:**
> What does the following output..

```
lscpu | grep "CPU op-mode(s)"
```

```

CPU op-mode(s):        32-bit, 64-bit

```

---

### Post by howefield on 2017-02-27
> **John_Patrick_Mason said:**
> ```

CPU op-mode(s):        32-bit, 64-bit

```

So you can run both 32 bit and 64 bit operating systems.

Running your first command without the grep will also give you details of the cpu capabilities.

```
sudo lshw -C cpu
```

Do you know what processor model you have ?

```
cat /proc/cpuinfo  | grep 'name'| uniq
```

Another method would be to boot with a 64 bit Live media - if it can't install 64 bit the media won't boot to the desktop ;)

---

### Post by RobGoss on 2017-02-27
Some Windows machine will support both 32 bit and a 64 bit, depending on your processor, if your using the correct command and it's telling you that you have a 64 bit, machine I would say stick with the results

---

### Post by John_Patrick_Mason on 2017-02-27
```
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
```

I could have swore that my machine was 32-bit. I think the initial confusion came when I checked out System Information in Windows XP Media Center Edition where it said that the OS type was 32-bit. Is it possible that Microsoft could have installed a 32-bit OS on 64-bit hardware?

---

### Post by RobGoss on 2017-02-27
If you see &#8220;32-bit operating system, x64-based processor,&#8221; this means you're using a 32-bit version of Windows 10 but your CPU can run a 64-bit version. If it doesn't say you have an x64-based processor, you have a 32-bit CPU and can't upgrade to the 64-bit

---

### Post by howefield on 2017-02-27
Hmm, not so sure now :)

[Intel(R) Pentium(R) 4 CPU 3.00GHz]("https://ark.intel.com/products/27497/Intel-Pentium-4-Processor-supporting-HT-Technology-3_00-GHz-1M-Cache-800-MHz-FSB")

Try booting the 64 bit media if you have one.

---

### Post by QIII on 2017-02-27
I think the Prescotts and Cedar Mills are 64bit.

---

### Post by RobGoss on 2017-02-27
That's correct if your machine boots to the live desktop of Ubuntu then you should be able to install it. I have a few old machine that are 32 bit and will not boot in to the 64 bit desktop of Ubuntu

---

### Post by John_Patrick_Mason on 2017-02-27
> **howefield said:**
> Hmm, not so sure now :)

[Intel(R) Pentium(R) 4 CPU 3.00GHz]("https://ark.intel.com/products/27497/Intel-Pentium-4-Processor-supporting-HT-Technology-3_00-GHz-1M-Cache-800-MHz-FSB")

Try booting the 64 bit media if you have one.

I have to create a bootable DVD first. Give me 15min. I'll let you know after if I can boot.

---

### Post by John_Patrick_Mason on 2017-02-27
So I created a live dvd with Ubuntu 14.04.5 installed. For some reason it didn't work the first time, so I tried a second time and managed to get it to work. Am I good to go then?

---

### Post by howefield on 2017-02-27
> **John_Patrick_Mason said:**
> Am I good to go then?

Yes, if the Live media of a 64 bit OS is booting to the desktop, then you are good to go. Were it a 32 bit pc the boot would have errored and not completed.

There may be other reasons why 64 bit might not be a good fit, eg lack of memory or other factors but it won't be because of the processor.

---

### Post by John_Patrick_Mason on 2017-02-27
OK, then. Thanks guys.

---

