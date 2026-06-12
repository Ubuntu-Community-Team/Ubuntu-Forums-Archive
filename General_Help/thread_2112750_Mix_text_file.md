---
title: "Mix text file"
date: 2013-02-05
forum: General Help
---

### Post by hunterlove22 on 2013-02-05
Hello everyone,

I have 2 file .txt containing email addresses. 
The first txt file has email with domain.net like [email]user1@domain.net[/email]
The second has email with domain.com like [email]user1@domain.com[/email]


Now i want to find and wrap the corresponding username for .net and .com in format:

 [email]user1@domain.net[/email] : [email]user1@domain.com[/email]

and save into a file.

Thanks in advanced

---

### Post by hunterlove22 on 2013-02-07
Please help me.

---

### Post by Vaphell on 2013-02-07
do these files match on a per line basis or are they unsorted? are there addresses which don't have their 2nd version in the other file?

---

### Post by hunterlove22 on 2013-02-07
> **Vaphell said:**
> do these files match on a per line basis or are they unsorted? are there addresses which don't have their 2nd version in the other file?

Not match on per line. But i use uniq to wrap all matching emails to on file also. Is there any way to bring them to that format?

in new txt file there will be

[email]user1@domain.net[/email]
[email]user1@domain.com[/email]
[email]user2@domain.net[/email]
[email]uesr2@domain.com[/email]

and so on.

---

### Post by steeldriver on 2013-02-07
I'm still finding it a bit difficult to understand exactly what you want to do - remember that the better you define the problem, the easier it is to solve

If your files look like this:

```
$ cat com.txt
user1@abcd.com
user2@efgh.com
user3@abcd.com
$
$ cat net.txt
user5@abcd.net
user2@efgh.net
user1@abcd.net
$

```then you could do something like

- read entries one at a time from one of the files
- search the other file for a 'match'
- if successful, output the 2 entries

e.g. using the bash shell + 'grep'

```

$ while read -r netaddr; do comaddr=$(grep -m1 -o "${netaddr%.net}.com" com.txt); if [ ! -z "$comaddr" ]; then echo "$netaddr" : "$comaddr"; fi; done < net.txt
user2@efgh.net : user2@efgh.com
user1@abcd.net : user1@abcd.com

```

---

### Post by hunterlove22 on 2013-02-07
Sorry for my bad explains. 
> 


now i would like to read 2 text files and wrap the matching username in format like

> aadrian@abc.net : [email]aadrian@abc.com[/email]

Thanks

---

### Post by fdrake on 2013-02-07
```

for i in $(cut -d "@" -f 1 com.txt); do netvar="$(grep $i net.txt)"; comvar="$(grep $i net.txt)"; echo "$netvar : $comvar" ; done;


```

AND YOU GET THESE:
> 
[email]aadrian@pfaonline.net[/email] : [email]aadrian@pfaonline.net[/email]
[email]aaflores@pfaonline.net[/email] : [email]aaflores@pfaonline.net[/email]
[email]aaimran@pfaonline.net[/email] : [email]aaimran@pfaonline.net[/email]
[email]aakinyemi@pfaonline.net[/email] : [email]aakinyemi@pfaonline.net[/email]
[email]aalbarran@pfaonline.net[/email] : [email]aalbarran@pfaonline.net[/email]



TO OUTPUT TO A FILE(united.txt) DO :
> 
for i in $(cut -d "@" -f 1 com.txt); do netvar="$(grep $i net.txt)"; comvar="$(grep $i net.txt)"; echo "$netvar : $comvar" >> united.txt; done;



there is also a little problem, when there is no match you get an empty line with ":" ate the beggining. you can fix that with "uniq united.txt > united2.txt" and you get only 1 blank line containing it.

---

### Post by hunterlove22 on 2013-02-08
> **fdrake said:**
> ```

for i in $(cut -d "@" -f 1 com.txt); do netvar="$(grep $i net.txt)"; comvar="$(grep $i net.txt)"; echo "$netvar : $comvar" ; done;


```

AND YOU GET THESE:


TO OUTPUT TO A FILE(united.txt) DO :


there is also a little problem, when there is no match you get an empty line with ":" ate the beggining. you can fix that with "uniq united.txt > united2.txt" and you get only 1 blank line containing it.

Thanks for your awesome reply. Btw, i need the format:

aadrian@abc.[COLOR="Red"]net[/COLOR] : aadrian@abc.[COLOR="red"]com[/COLOR]

---

### Post by fdrake on 2013-02-08
> **hunterlove22 said:**
> Thanks for your awesome reply. Btw, i need the format:

aadrian@pfaonline.[COLOR="Red"]net[/COLOR] : aadrian@pfaonline.[COLOR="red"]com[/COLOR]
my bad I misstyped the name file(change one of the net.txt to com.txt): it should have been:
```

for i in $(cut -d "@" -f 1 com.txt); do netvar="$(grep $i net.txt)"; comvar="$(grep $i com.txt)"; echo "$netvar : $comvar" ; done;


```

---

### Post by HermanAB on 2013-02-08
Load the files into a spreadsheet like gnumeric. you can go crazy in there and then save as csv

---

### Post by hunterlove22 on 2013-02-08
> **fdrake said:**
> my bad I misstyped the name file(change one of the net.txt to com.txt): it should have been:
```

for i in $(cut -d "@" -f 1 com.txt); do netvar="$(grep $i net.txt)"; comvar="$(grep $i com.txt)"; echo "$netvar : $comvar" ; done;


```

Yes, i did change before but not as expected. 

>  : [email]11test@pfaonline.com[/email]
 : [email]122151235235@pfaonline.com[/email]
 : [email]123122123@pfaonline.com[/email]
 : [email]1242145125@pfaonline.com[/email]
[email]168lasvegas@pfaonline.net[/email]
 : [email]168lasvegas@pfaonline.com[/email]
 : [email]1stconsulting@pfaonline.com[/email]
 : [email]21w4114123@pfaonline.com[/email]



Btw, i tried to use

> awk -F'@' 'NR==FNR{a[$1]=$0;next}$1 in a{print a[$1]" : "$0}' net.txt com.txt

And the result is a bit better

> 168lasvegas@pfaonline.net
 : [email]168lasvegas@pfaonline.com[/email]
[email]2hlusiana@pfaonline.net[/email]
 : [email]2hlusiana@pfaonline.com[/email]
[email]2jsent@pfaonline.net[/email]
 : [email]2jsent@pfaonline.com[/email]
[email]aadrian@pfaonline.net[/email]
 : [email]aadrian@pfaonline.com[/email]
[email]aaflores@pfaonline.net[/email]
 : [email]aaflores@pfaonline.com[/email]
[email]aaimran@pfaonline.net[/email]
 : [email]aaimran@pfaonline.com[/email]
[email]aakinyemi@pfaonline.net[/email]
 : [email]aakinyemi@pfaonline.com[/email]


btw, they are on in a line. Do you know why and how to fix it?

Thanks

---

### Post by fdrake on 2013-02-08
i do not get them in different line like you. something must be wrong because i do not get the names in different lines with both commands . 
> 
user@t61:~$ awk -F'@' 'NR==FNR{a[$1]=$0;next}$1 in a{print a[$1]" : "$0}' net.txt com.txt
 : 
 : 
 : 
 : 
[email]aadrian@pfaonline.net[/email] : [email]aadrian@pfaonline.com[/email]
 : 
[email]aaflores@pfaonline.net[/email] : [email]aaflores@pfaonline.com[/email]
 : 
[email]aaimran@pfaonline.net[/email] : [email]aaimran@pfaonline.com[/email]
 : 
[email]aakinyemi@pfaonline.net[/email] : [email]aakinyemi@pfaonline.com[/email]
 : 
[email]aalbarran@pfaonline.net[/email] : [email]aalbarran@pfaonline.com[/email]
user@t61:~$ 





do you have spaces after the email text?  that is the only possible reason I can think of

---

### Post by hunterlove22 on 2013-02-08
> **fdrake said:**
> i do not get them in different line like you. something must be wrong because i do not get the names in different lines with both commands . 




do you have spaces after the email text?  that is the only possible reason I can think of


Thanks. That's problem with terminal in backtrack. a bit weird. I checked in my server and that's fine. Thank you so much for your help.

---

