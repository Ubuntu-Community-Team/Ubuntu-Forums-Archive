---
title: "Help needed with sed command"
date: 2013-06-17
forum: General Help
---

### Post by Mariane on 2013-06-17
Hi, 

I apologize if this is a silly question. How can you change multiple occurences of a string? 

I want to replace the string /var/www/prestashop with the string /var/www/ma-hotte-deco

And the string 178.170.117.59/prestashop/ with the string 178.170.117.59/ma-hotte-deco

Both type occur many times, in several different subdirectories. Some of them are nested in cache/something/1/1//1/1//1/1/0/1/0/22/45/ and when I finally reach the directory, there is only one file there and I have to go back a long way then up again in a crazy list of sub directories to find the next file where changes should be made... I would do it by hand but these directories are driving me crazy. 

Following advice given here:
[http://askubuntu.com/questions/20414/find-and-replace-text-within-a-file-using-commands](http://askubuntu.com/questions/20414/find-and-replace-text-within-a-file-using-commands)

I tried:
```

sed -i 's/"var/www/prestashop"/"var/www/ma-hotte-deco"/g' *
sed -i s/"var/www/prestashop"/"var/www/ma-hotte-deco"/g *
sed -i s/'var/www/prestashop'/'var/www/ma-hotte-deco'/g *

```

Each time I get the answer: sed: -e expression #1, char 12: unknown option to `s'

(or char 13)

Telling me how to do it would be very kind, sparing the time to tell me why it should be written in such or such a way, and not the way I wrote it, would be super kind :)

---

### Post by matt_symes on 2013-06-17
Hi

You can escape the forward slashes with back slashes but i prefer to use a different character with file paths for readability

```
sed  -i 's:/var/www/prestashop:/var/www/ma-hotte-deco:g' *
```

For a qucik example... (the : character becomes the delimiter.

```

matthew-S206:/home/matthew % cat tmp 
 /var/www/prestashop
 /var/www/prestashop
 /var/www/prestashop
matthew-S206:/home/matthew % sed  's:/var/www/prestashop:/var/www/ma-hotte-deco:g' tmp
 /var/www/ma-hotte-deco
 /var/www/ma-hotte-deco
 /var/www/ma-hotte-deco
matthew-S206:/home/matthew % 
```

For escaping the backslash character.

```
sed -i  "s/\/var\/www\/prestashop/\/var\/www\/ma-hotte-deco/g" *
```

Kind regards

---

### Post by Cheesemill on 2013-06-17
You can use a different character for the delimiter, in this case I've used the | character.
```
sed -i 's|var/www/prestashop|var/www/ma-hotte-deco|g' *
```

You can use this with find to run the command on all files below a certain directory...
```
find /root/search/directory -type f -exec sed -i 's|var/www/prestashop|var/www/ma-hotte-deco|g' '{}' \;
```

---

### Post by Mariane on 2013-06-17
Thank you very much, both of you. 
The
```

find ./ -type f -exec sed -i 's|var/www/prestashop|var/www/ma-hotte-deco|g' '{}' \;

```
command was particularly usefull as it made sed recursive :D 

One more question, please. Why does it has to be written with a semicolon at the end? I think it is the first time I see that on a command-line. What does the semicolon mean?

---

### Post by matt_symes on 2013-06-17
Hi

The find command needs the semi-colon at the end as it delimits the end of the -exec option.

It also needs to be escaped with the back-slash character.

Kind regards

---

