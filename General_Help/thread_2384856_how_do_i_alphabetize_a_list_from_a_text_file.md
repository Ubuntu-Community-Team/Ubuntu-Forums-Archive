---
title: "how do i alphabetize a list from a text file?"
date: 2018-02-13
forum: General Help
---

### Post by ardouronerous on 2018-02-13
I have a list of names and contact numbers that is in a txt file, however, the names aren't alphabetized and makes it difficult to navigate through, how do I alphabetize the list?

I'm running Lubuntu 16.04.

---

### Post by sudodus on 2018-02-13
Please show a typical line from your text file and tell us how you want to alphabetize it. (I would guess that you want to sort it by first name or family name, but I don't know where you have the names in your text files.)

---

### Post by vasa1 on 2018-02-13
> **sudodus said:**
> Please show a typical line from your text file and tell us how you want to alphabetize it. (I would guess that you want to sort it by first name or family name, but I don't know where you have the names in your text files.)

+1

The more data OP shares, the easier it will be to answer correctly. Otherwise, one can recommend 
*man sort* or other online resources such as 
[https://www.computerhope.com/unix/usort.htm](https://www.computerhope.com/unix/usort.htm) or 
[https://www.ibm.com/developerworks/community/blogs/58e72888-6340-46ac-b488-d31aa4058e9c/entry/linux_sort_command_sort_lines_of_text_files9?lang=en](https://www.ibm.com/developerworks/community/blogs/58e72888-6340-46ac-b488-d31aa4058e9c/entry/linux_sort_command_sort_lines_of_text_files9?lang=en) or
[https://en.wikipedia.org/wiki/Sort_(Unix)](https://en.wikipedia.org/wiki/Sort_(Unix))

---

### Post by TheFu on 2018-02-13
> **ardouronerous said:**
> I have a list of names and contact numbers that is in a txt file, however, the names aren't alphabetized and makes it difficult to navigate through, how do I alphabetize the list?

I'm running Lubuntu 16.04.

**sort**, but this sounds like a homework question.

---

### Post by ardouronerous on 2018-02-13
The list is like this;
```
Sarandon, Susan - XXX-XXX-XXX
Cruise, Tom - XXX-XXX-XXX
Bale, Christian - XXX-XXX-XXX
Goldblum, Jeff - XXX-XXX-XXX
```

As you can see the list isn't in alphabetical order, I'd like to alphabetize the list.

---

### Post by sudodus on 2018-02-13
If you want to sort according to family name, it is very easy. Assume that the list is in a file with the name unsorted-list.txt,

```

sort unsorted-list.txt > sorted-list.txt

```

and the sorted (alphabetized) result is in the file sorted-list.txt.

---

### Post by ardouronerous on 2018-02-13
Thank you, that worked! :)

---

### Post by Buntu Bunny on 2018-02-14
gedit will alphabetize a list for you too.

---

### Post by vasa1 on 2018-02-14
As will LibreOffice Calc and Geany.

---

### Post by coffeecat on 2018-02-14
... LibreOffice Writer and Pluma too.... :)

By the way, you need to activate the sort plugin in preferences in both gedit and pluma before sort appears in their menus. Or at least I had to in Ubuntu 16.04.

---

### Post by vasa1 on 2018-02-14
In Geany 1.27 (the version in 16.04), select the text then Edit > Format > Send to > sort -u (or to a custom command if the user has set up one).

I used Gedit quite a bit until an update rendered several plug-ins non-functional by design.

---

