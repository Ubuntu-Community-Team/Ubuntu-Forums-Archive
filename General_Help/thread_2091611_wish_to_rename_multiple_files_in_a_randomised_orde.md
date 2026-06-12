---
title: "wish to rename multiple files in a randomised order"
date: 2012-12-05
forum: General Help
---

### Post by ask_ on 2012-12-05
Hello.

I have a few files in a folder. They are named 1.mp3 , 2.mp3 , 3.mp3 and so on. I wish to rename these using a random key (which is basically a permutation on 12345678 , for example 34281765 , so 1.mp3 becomes 3.mp3 , 2.mp3 becomes 4.mp3 and so on). Is there a way I can use shell scripts to do so. I am bit of a beginner when it comes to shell scripts. What sort of approach should I use.

(I just want to record a few sounds,:guitar:, and be able to recognize them later. But since I would be the one who names them, I will already know them by name, hence wish to shuffle them a bit )

Thanks.

---

### Post by hwttdz on 2012-12-05
Bash scripting goodness. You'll have to change the magic number to change the ordering, and change the echo line to just a move line to make it do what it says it will.  It's important that the magic number has the same number of characters as you have files.

```
for i in `ls *.mp3`
do
j=`basename $i .mp3`;
k=`echo 34281765|cut -c $j`;
echo "mv $i $k.mp3";
done
```

---

### Post by steeldriver on 2012-12-05
wouldn't it be easier to *select *a random file each time?

```
shuf -n1 -e *.mp3
```

---

### Post by ask_ on 2012-12-05
> **hwttdz said:**
> Bash scripting goodness. You'll have to change the magic number to change the ordering, and change the echo line to just a move line to make it do what it says it will.  It's important that the magic number has the same number of characters as you have files.

```
for i in `ls *.mp3`
do
j=`basename $i .mp3`;
k=`echo 34281765|cut -c $j`;
echo "mv $i $k.mp3";
done
```

It works . I tried the code with a few text files and they did get randomly renamed , based on the key , that is. Now I have another query, how can I perform the inverse operation. I guess , I will have to use the same code but with the key which is inverse permutation of the original key. What say ? :D (Although come to think of it ,I wonder if I will need to do the inverse operation , as my work with the files would be over after I listen to them. But all that's unimportant. :) )
Thanks for the reply. It helped a lot.

---

### Post by ask_ on 2012-12-05
> **steeldriver said:**
> wouldn't it be easier to *select *a random file each time?

```
shuf -n1 -e *.mp3
```

Hi. Thanks for the reply.

Will try this out too.

---

### Post by steeldriver on 2012-12-05
just to explain a bit more, suppose you wanted to 'do something' (e.g. play) to your files in random order, you could make a loop like

```
while read -r -d $'\0' file; do echo "$file"; done < <(shuf -ze *.mp3)
```I'm just echoing the filename here but you get the idea

many media players have a built in shuffle mode of course - this is just for fun ;)

---

### Post by ask_ on 2012-12-06
> **steeldriver said:**
> 

many media players have a built in shuffle mode of course - this is just for fun ;)

It seems what I wanted to accomplish could be done in more and more simpler ways , :o . Not that I wasn't aware of shuffle mode  , but didn't think of it at first at all. Talk about complicating things. But anyways, got to learn some new shell commands. :D .

---

