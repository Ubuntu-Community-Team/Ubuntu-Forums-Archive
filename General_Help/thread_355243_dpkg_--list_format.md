---
title: "dpkg --list format?"
date: 2007-02-07
forum: General Help
---

### Post by peter360 on 2007-02-07
I am new to Ubuntu.  Can someone explain the output lines of the following command to me?  I read the dpkg manual page, also searched on internet but did not find documentation on the output format of dpkg --list.

$ dpkg --list ssh
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                      Version                   Description
+++-=========================-=========================-==================================================================
un  ssh                       <none>                    (no description available)

to be more specific:
1.  I am guessing the first 3 lines are verbosely echoing the query I entered.  Right?
2.  "un" in the first column means what?
3.  What are those "|", "|/" and "||/" signs btw?  I assume they have no other meaning than to format the text, but it looks like a weird way -- wouldn't it be more visually appealing to make the lines left aligned?

Thanks

---

### Post by Polygon on 2007-02-07
i get the same output as well

> mark@ubuntu:~$ dpkg --list ssh
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  ssh            <none>         (no description available)
mark@ubuntu:~$

i am not sure what the top output is talking about, but i know the bottom is saying that ssh is not installed. I just installed ssh real fast and i get this at the bottom now:

> 
ii  ssh            4.3p2-5ubuntu1 Secure shell client and server (transitional


and im guessing the || ||\ and ii things are just prefixes that show what type of message it is, im guessing ii = information, etc. Similar to xorg which uses (EE) (WW) (||), etc

---

### Post by dagnabit dang doohickey on 2007-02-07
The output on the top is the column descriptions (and possible values.) The ||/ stuff are column pointers pointing down to the values. The value i represents Install (or Installed, depending on the column), and so on.

---

### Post by peter360 on 2007-02-10
> 
The output on the top is the column descriptions (and possible values.) 


Well, for example, which column is the first line
> 
Desired=Unknown/Install/Remove/Purge/Hold


describing?  I don't see a column named "Desired"...


> 
The ||/ stuff are column pointers pointing down to the values. The value i represents Install (or Installed, depending on the column), and so on.


It is pretty hard for me to visualize those signs as pointers...  So according to you, the value "ii" as in polygon's post really are two "i"s in two seperate columns?

Are there any documentation on this format?

---

### Post by peter360 on 2007-02-10
OK, I believe I have figured it out -- with the help from dagnabit's post.  Basically, in my original example, the first column is "Desired" with the value "u" meaning "Unknown", the second column is "Status" with the value "n" meaning "Not (installed)".  The third column is "Err" with an empty value.  The remaining columns are straight forward.   You have to read the "|" and "/" signs vertically to make sense of them.  Presumably the author of dpkg designed this format so the first 3 columns can be represented compactly.  

Maybe I am slow in getting this, but I have to say this representation is not the most intuitive.   I guess I am not the only person confused.  At least some explanation should be included in the manual page...

---

