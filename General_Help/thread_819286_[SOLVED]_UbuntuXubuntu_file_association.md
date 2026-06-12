---
title: "[SOLVED] Ubuntu/Xubuntu file association"
date: 2008-06-05
forum: General Help
---

### Post by unicorn_2003_1 on 2008-06-05
Hi guys, I have Xubuntu 8.04 on my machine. I know I can rightclick a file, and make an application as the default one to open a certain file. But is there a centralized way to manage your file association settings? or do you know where Ubuntu store this kind of configuration files?

Thanks.

---

### Post by rraj.be on 2008-06-05
You can do this using the following


```
System--> Preferences-->  assistive technologies
```


There click
```

            PREFERRED APPLICATIONS
```

You can set defaults there.

Hope this helped you.

---

### Post by unicorn_2003_1 on 2008-06-05
Thank Raj, but my system is Xubuntu. The desktop environment is Xfce 4.4, I checked Settings->Settings Manager->Preferred Applications. But it only has options for default web browser and mail reader. 

Do you know where *buntu store its file association file? I guess I can manually edit it.

---

### Post by rraj.be on 2008-06-05
Generally all your user setting will be store in 

/home/<your user name>


But it will be hidden.

You can view it by checking show hidden files fro view option.

But i dont know exactly where all these setting will be stored.

I think each package has its own setting and will be save in file named 

[ " .<package name>"    ]

---

### Post by unicorn_2003_1 on 2008-06-05
Thanks. I'm now looking at this File Types Editor ([http://www.kdau.com/projects/assogiate]("http://www.kdau.com/projects/assogiate/"))

This application is also in the Ubuntu repository, so I think it'd be safe to use.

Next stop, heading to how to make Firefox open various protocols and files without resorting to "about:config"

---

### Post by rraj.be on 2008-06-05
Yes i have too  seen that.

A bit usedfull tool

---

