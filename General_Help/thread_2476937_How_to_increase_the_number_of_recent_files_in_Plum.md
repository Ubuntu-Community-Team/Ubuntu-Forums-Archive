---
title: "How to increase the number of recent files in Pluma from its default of 5?"
date: 2022-07-12
forum: General Help
---

### Post by Tom_Carr on 2022-07-12
I am running ubuntu 22.04.  I am using pluma which I like better than the text editor included with ubuntu.  I want to increase the number of recent files in Pluma from its default of 5.  I found this solution online

$ gsettings set org.mate.pluma max-recents 10
$ gsettings get org.mate.pluma max-recents 10

I don't understand this code so I don't know if it is safe to do this.  So that is my question.  Is the above code safe?

I got it from here:

[https://askubuntu.com/questions/885103/how-to-increase-the-number-of-recent-files-in-pluma-from-its-default-of-5](https://askubuntu.com/questions/885103/how-to-increase-the-number-of-recent-files-in-pluma-from-its-default-of-5)

---

### Post by #&amp;thj^% on 2022-07-12
Yep, I set mine at 15
```
me on Tue Jul 12 at 11:08 AM in ~ branch: (HEAD) 
>> gsettings set org.mate.pluma max-recents 15


me on Tue Jul 12 at 11:08 AM in ~ branch: (HEAD) 
>>  gsettings get org.mate.pluma max-recents
uint32 15


me on Tue Jul 12 at 11:08 AM in ~ branch: (HEAD) 
>> 

```
Have Fun
EDIT:gsettings is a sytem utility for dconf , if you prefer a GUI use dconf-editor, the first command sets the value, the get command verify's the change.

---

### Post by mIk3_08 on 2022-07-14
> **Tom_Carr said:**
> 
$ gsettings set org.mate.pluma max-recents 10
$ gsettings get org.mate.pluma max-recents 10

Thanks for sharing. I might use this command soon. Regards and cheers.

---

