---
title: "Ubuntu 18.04 &#23433;&#35037;floodlight and input ant compile failed"
date: 2020-01-09
forum: General Help
---

### Post by lamtw1040 on 2020-01-09
Hi, I want to install floodlight controller. First, I need to install ***environment of java*** and ***ant*** before install floodlight controller.
However, when I want to install ***environment of java*** and ***ant***, I was failed. And then, I referenced the following URL:
[https://www.cnblogs.com/pullself/p/10259420.html](https://www.cnblogs.com/pullself/p/10259420.html)
 
 
Firstly, I used terminal to input the following instruction.

```
sudo apt-get install build-essential default-jdk ant python-dev
```
```
sudo git clone git://github.com/floodlight/floodlight.git
```
```
cd floodlight
```

Secondly, when I input the following instruction, I got the following problem
```
sudo ant
```
 
Buildfile: /home/lamtw/floodlight/build.xml
[taskdef] Could not load definitions from resource tasks.properties. It could not be found.

[ATTACH=CONFIG]284770[/ATTACH]

Therefore, I am following URL to input the following instruction:
```
sudo git checkout v0.90
```
Then, I input sudo ant again, but I got another problem:
[ATTACH=CONFIG]284771[/ATTACH]

I don’t know what to solve these problems. I hope you can help me. Thank you~~

---

### Post by slickymaster on 2020-01-09
[I]Thread moved to **General Help**.

[/I]Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

