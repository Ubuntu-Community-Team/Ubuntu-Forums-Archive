---
title: "MD5 Checksum"
date: 2006-10-26
forum: General Help
---

### Post by dontgetshocked on 2006-10-26
How can I check the checksum of the file, MD5 wont work on Ubuntu
Is there other software or a command to do this?

---

### Post by PriceChild on 2006-10-26
```
md5sum <<name of file>>
```

---

### Post by daedalusman on 2006-10-26
Similar question, how can I get an md5 checksum for a word? I need this to setup mpdscribble correctly. Thanks.

---

### Post by grte on 2006-11-17
> **daedalusman said:**
> Similar question, how can I get an md5 checksum for a word? I need this to setup mpdscribble correctly. Thanks.

Use the following command:

```
echo -n 'password' | md5sum
```

Naturally, replace password with your password (keep the quotes, though.)

This will give you something like the following output:

```
5f4dcc3b5aa765d61d8327deb882cf99  -
```

In that example, 5f4dcc3b5aa765d61d8327deb882cf99 would be the md5 sum of your password.  Don't include the following spaces or dash.

---

### Post by owerio on 2007-04-04
I want to check the md5sum from the text file, how can I do that? Thanks

---

### Post by Ramses de Norre on 2007-04-04
You mean like you downloaded an ISO and an md5file and want to check for consistency? If so, save both in the same directory, with the same name and give the md5file the same name with ".md5" added (or use the correct syntax in the file, being "md5sum filename").
Now run **md5sum -c *file.md5***, you'll hopefully get the output "OK".

---

### Post by owerio on 2007-04-04
> **Ramses de Norre said:**
> You mean like you downloaded an ISO and an md5file and want to check for consistency? If so, save both in the same directory, with the same name and give the md5file the same name with ".md5" added (or use the correct syntax in the file, being "md5sum filename").
Now run **md5sum -c *file.md5***, you'll hopefully get the output "OK".

Thanks for the reply. Actually I dont have a special md5file. I just created a text file and pasted the md5 string in it. Then added the .md5 extension to filename but the terminal didnt accepted that md5 file as valid. 
> 
(or use the correct syntax in the file, being "md5sum filename").
Actually I didnt understand here. Is this the way to convert the text file into a md5 file? 

Lastly the file that wil be md5 checked is a tar.gz .

---

### Post by Ramses de Norre on 2007-04-04
No, you need to add your md5sum in the file like this example: ```
568fc375b37d8bc6e44c6f518ecd6ab5  Archlinux-i686-0.8-Voodoo.current.iso


```
(Watch the newline), the second string is of course the filename of the file to check and this is all saved in a file called Archlinux-i686-0.8-Voodoo.current.iso.md5.

---

