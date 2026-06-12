---
title: "GDM restart when I try to type password"
date: 2005-10-20
forum: General Help
---

### Post by gtdj on 2005-10-20
When I try to login via GDM, my X restart while I type first character of password.

How can I solve this problem ?

---

### Post by piggyaugu on 2005-10-21
well

I have exactly the same pb than you. 

still searching for answer..............

---

### Post by TheVicious on 2005-10-21
The same thing started happening for me after I installed 'Verdana' font from windows and did 'sudo dpkg-reconfigure fontconfig'. Almost every application started to crash, including the gnome greeter.

---

### Post by gtdj on 2005-11-06
[QUOTE=TheVicious]The same thing started happening for me after I installed 'Verdana' font from windows and did 'sudo dpkg-reconfigure fontconfig'. Almost every application started to crash, including the gnome greeter.[/QUOTE]

Yeah ! thx for your assistance, I found the problem. I try to remove last fonts I have installed (rm my fonts in /usr/share/fonts/truetype/...) and then fc-cache -f -v. Restart after that, at last it works ! :D

---

### Post by Peacepunk on 2006-03-25
Confirmed;

In cases you manually added special fonts in 

```
/usr/share/fonts/truetype/ 
```

 & even with proper edit of the "fonts.cache-1" file, you can end up with the above mentionned problem.

I used the above instruction to remove a self created "winf" file (containing "times new roman, comic sans ms & Garamond") as well as two more folders with Khmer (Cambodian) fonts, Limon and KhmerOS.

On the ther hand, it is safe to remove unneccessary fonts from this folder: I did get rid of a lot of "gujarat" or "tamil" fonts & the likes.

My current list in /usr/share/fonts/truetype now only displays 

-baekmuk
-freefont
-openoffice
-ttf-bitsream-vera

& that's enough for the Greeter App to stop bugging like described above.

reminder:

- Start Ubuntu in Safe/recovery mode
- Wait for root@name_of_your_machine

```
 dir /usr/share/fonts/truetype 
```

- Check the results, write down unecessary files' names

- Then, one by one if you added several,

```
 rm -R /usr/share/fonts/truetype/*name of the folders you added yourself*
```

- check again;

```
 dir /usr/share/fonts/truetype 
```

- when finish, cd/

&

```
reboot
```

**Unanswered questions:**

- This is a workaround. How to safely add fonts ?

- Why is Greeter tied to Truetype fonts. Is there a way to change this ?

*OffTopic:*
- My first idea was to restore to original settings using a copy of "truetype' folder from my laptop: I was never able to access my USB Fashdrive in recovery mode.


Cheers.

---

