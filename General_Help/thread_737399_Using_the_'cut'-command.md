---
title: "Using the 'cut'-command"
date: 2008-03-27
forum: General Help
---

### Post by Ballena on 2008-03-27
Hi

Is there a way to use the command 'cut' to cut of the last character of a word with unknown length? Like 'echo ape | cut -c 1-(N-1) where N is the number of charters. The desired result would be that it prints out 'ap'.

---

### Post by nick_h on 2008-03-27
No, but you could use *sed* as follows:
```
echo ape | sed 's/.$//'
```

---

### Post by Gwasanaethau on 2008-03-27
> **Ballena said:**
> Hi

Is there a way to use the command 'cut' to cut of the last character of a word with unknown length? Like 'echo ape | cut -c 1-(N-1) where N is the number of charters. The desired result would be that it prints out 'ap'.

I think you can also do it with 'cut', but you need to declare a variable first:
```
WORD=ape
echo $WORD | cut -c 1-$(echo "${#WORD} - 1" | bc)
```
Admittedly it's a little long-winded, but it should work!

NB:
${#WORD} represents the length of the word contained in the variable 'WORD'. In this case, it would be 3, as 'ape' has three letters.

---

### Post by nick_h on 2008-03-27
> Admittedly it's a little long-winded, but it should work!
An interesting approach :)

If you are using a variable then you could use the following:
```
WORD=ape; echo ${WORD%?}
```

---

### Post by Gwasanaethau on 2008-03-27
> **nick_h said:**
> An interesting approach :)

If you are using a variable then you could use the following:
```
WORD=ape; echo ${WORD%?}
```
Ah! Very clever - didn't know about that now! Thanks a mill!

---

### Post by Ballena on 2008-03-28
Thanks for all the answers!

---

