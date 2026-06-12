---
title: "Set new window to open in the center of the screen"
date: 2014-01-18
forum: General Help
---

### Post by matospalka on 2014-01-18
Hi,

when I open new window in Lubuntu, its everytime in different place - I would like to set new window to be opened in the center.

Where can I change it?

Thanks

---

### Post by vasa1 on 2014-01-18
Read this: [https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse](https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse)
It should help :)

---

### Post by matospalka on 2014-01-18
> **vasa1 said:**
> Read this: [https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse](https://help.ubuntu.com/community/Lubuntu/Windows#Reposition_and_Resize_Windows_Without_Using_a_Mouse)
It should help :)

Thanks, but I dont want to press any key to have new opened window in the center. I would like to have it default without any need of action from me. But thanks anyway...

Is there any way how to do it automaticaly?

---

### Post by vasa1 on 2014-01-19
> **matospalka said:**
> Thanks, but I dont want to press any key to have new opened window in the center. I would like to have it default without any need of action from me. But thanks anyway...

Is there any way how to do it automaticaly?
Pllease read [https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized](https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized) as well. 
That link and the links it points to do explain how to do so automatically. I strongly recommend you read at least [http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) very carefully because the file it refers to is crucial to put you in control. Anyway, let's assume you've read the wiki link.

After taking the appropriate cautions described in the wiki, insert the following code into your ~/.config/openbox/lubuntu-rc.xml just above the second-last line of the file (which should contain just **</applications>**):

```
    <application type"normal">
      <position>
        <x>center</x>
        <y>center</y>
      </position>
    </application>
```
Now, when you reconfigure Openbox, all applications should open in the center of your screen.

---

### Post by matospalka on 2014-01-19
I tried it, and when reconfigure Openbox I have message about error with Extra content at the end of the file... I put your content just above [B]"[B]</applications>" :-k

[/B]
[/B]

---

### Post by vasa1 on 2014-01-19
> **matospalka said:**
> I tried it, and when reconfigure Openbox I have message about error with Extra content at the end of the file... I put your content just above [B]"[B]</applications>" :-k

[/B]
[/B]

I'm very sorry about that. There was a mistake in the code. I left out "=" in the first line.
```
    <application type="normal">
      <position>
        <x>center</x>
        <y>center</y>
      </position>
    </application>
```
Please try this ^.

---

### Post by matospalka on 2014-01-19
Wow, now it work perfect! Thank you very much!

---

### Post by vasa1 on 2014-01-19
> **matospalka said:**
> Wow, now it work perfect! Thank you very much!
Great! Openbox is wonderful and lubuntu-rc.xml is a big part of it. Do try to get to know it as much as you can :)

---

