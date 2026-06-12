---
title: "splitting files?"
date: 2007-06-22
forum: General Help
---

### Post by dansued on 2007-06-22
I have a 16 GB HDD image file that I want to back up on dvd. I have tried Gnomebaker and Xfburn but they either can't see the image file or can't split it up.

Is there a DVD burning program that can split it up automatically?

Or

I know in Windows I could rar them into 4.7 GB chunks, is there something like that in ubuntu? It's a pretty critical image file so I don't want to do anything that has the possibility of corrupting it.

---

### Post by McNils on 2007-06-23
I do not know a DVD burning tool that split a large image to a collection of smaller chunks, 

But you can split the image usisg **split**. See **man split**. To recreate the image you can use **cat**.

```

cat chunk1 > img
cat chunk2 >> img
....

```

---

### Post by rommel_rco on 2007-09-17
install rar by typing to the terminal 

sudo apt-get install rar 
or search for *rar* via Synaptic Package Manager

then to split the file type
rar a -v1024k fileoutput filetobesplitted
rar a -v10m fileoutput filetobesplitted

it will split the file named *filetobesplitted* into 1024KB=1MB with the output filename *fileoutput*
or split it into megabytes, the second one is splitting into 10megabytes for more info type [B][I]man rar

[/I][/B]

---

