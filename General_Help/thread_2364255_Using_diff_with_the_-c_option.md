---
title: "Using diff with the -c option"
date: 2017-06-20
forum: General Help
---

### Post by John_Patrick_Mason on 2017-06-20
I don't quite understand the output of the diff command with the -c  option.
If I create two files: file1.txt and file2.txt that contain the following:

```

cat -A file1.txt
I need to go to the store.$
I need to buy some apples.$
When I get home, I'll wash the dog.$
I promise.$

cat -A file2.txt:
I need to go to the store.$
I need to buy some apples.$
When I get home, I'll wash the dog.$

```

when I try to use diff with the -c option I get:

```

diff -c file1.txt file2.txt
*** file1.txt   2017-06-14 20:30:13.953415914 -0400
--- file2.txt   2017-06-13 21:30:45.309853585 -0400
***************
*** 1,4 ****
  I need to go to the store.
  I need to buy some apples.
  When I get home, I'll wash the dog.
- I promise.
--- 1,3 ----

```

as expected, since file2.txt does not have a fourth line:

```

diff -y file1.txt file2.txt
I need to go to the store.                                             I need to go to the store.
I need to buy some apples.                                             I need to buy some apples.
When I get home, I'll wash the dog.                                    When I get home, I'll wash the dog.
I promise.                                                           <


```

However, if I modify the third line in file1.txt to: "I need to call a friend," thereby giving me:

```

diff -y file1.txt file2.txt
I need to go to the store.                                             I need to go to the store.
I need to buy some apples.                                             I need to buy some apples.
I need to call a friend.                                             | When I get home, I'll wash the dog.
I promise.                                                           <



```

I don't quite get the output of the diff command with -c option:

```

*** file1.txt   2017-06-14 20:39:44.193376149 -0400
--- file2.txt   2017-06-13 21:30:45.309853585 -0400
***************
*** 1,4 ****
  I need to go to the store.
  I need to buy some apples.
! I need to call a friend.
! I promise.
--- 1,3 ----
  I need to go to the store.
  I need to buy some apples.
! When I get home, I'll wash the dog.

```

The ! before the third lines in file1 and file2 makes sense since "I need to call a friend" is different from "When I get home, I'll wash the dog."

```

diff -y file1.txt file2.txt
I need to go to the store.                                               I need to go to the store.
I need to buy some apples.                                               I need to buy some apples.
I need to call a friend.                                               | When I get home, I'll wash the dog.
I promise.                                                                                          <

```

What I don't get is the ! before the fourth line in file1.txt when I type diff -c.
If I look at the output of diff -y above, the diff command tells me that file2.txt has no fourth line.
So you come there is an ! before the fourth line instead of a - (minus) ?
After all the fourth line in file2 is empty according to the output of diff -y.

---

### Post by John_Patrick_Mason on 2017-06-21
Thread bumped...

---

### Post by papibe on 2017-06-21
Hi John_Patrick_Mason.

Here's some information it could be useful: [https://www.computerhope.com/unix/udiff.htm](https://www.computerhope.com/unix/udiff.htm)

However, besides identifying the meaning of **+**, **-** and **!**, it looks like **!** (grouping) is not the most useful tag.

Hope it helps.
Regards.

---

### Post by John_Patrick_Mason on 2017-06-21
> **papibe said:**
> 
Here's some information it could be useful: [https://www.computerhope.com/unix/udiff.htm](https://www.computerhope.com/unix/udiff.htm)


I'm already familiar with the link you provided. That's how I originally got to learn what the output of diff with no options meant. Personally, I much prefer the output of diff -u; it's much clearer.
What do you think specifically triggers the ! tag? Correct me if I'm wrong, but it seems that if a line in file1 differs from a line in file2, diff will tag both lines, in addition to any lines that follow, with a !, *until it finds lines that do match. *If, however, both lines match, it will add a + or - instead, according to the situation.

---

### Post by Habitual on 2017-06-22
"$" is a metacharacter?
add . to it and IDK what. 

Just sayin'

---

### Post by John_Patrick_Mason on 2017-06-22
> **Habitual said:**
> "$" is a metacharacter?
add . to it and IDK what. 

Just sayin'

I'm not sure if I understand your post, Habitual. The dollar sign at the end of each line is meant to indicate where the line ends, like, if there are any spaces between the dot and the end-of-line character. I used cat with the -A option because I wanted people to be able to exactly reproduce the same file that I had. If you're asking whether the dollar sign can be a metacharacter, then the answer is yes. The dollar sign is used in arithmetic and parameter expansion, as well as command substitution. See page 70 of [this]("http://linuxcommand.org/tlcl.php") book for more details.

---

### Post by Habitual on 2017-06-22
I have never used cat with an -A switch.
Sorry about the intrusion.
Thanks for the link.

---

### Post by John_Patrick_Mason on 2017-06-22
> **Habitual said:**
> 
Thanks for the link.

No problem.

---

### Post by papibe on 2017-06-23
> **John_Patrick_Mason said:**
> Personally, I much prefer the output of diff -u; it's much clearer.
Yes, I agree :)
> **John_Patrick_Mason said:**
> Correct me if I'm wrong, but it seems that if a line in file1 differs from a line in file2, diff will tag both lines, in addition to any lines that follow, with a !, *until it finds lines that do match. *If, however, both lines match, it will add a + or - instead, according to the situation.
Yes, it seems that way.

+ and - are use for lines that can be added or removed. ! looks to be used to group lines that are different.

Just my thoughts.
Regards.

---

### Post by John_Patrick_Mason on 2017-06-23
> **papibe said:**
> Yes, I agree :)

Yes, it seems that way.

+ and - are use for lines that can be added or removed. ! looks to be used to group lines that are different.

Just my thoughts.
Regards.

Thanks, papibe. I'm marking this thread as solved.

---

