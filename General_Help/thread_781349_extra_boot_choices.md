---
title: "extra boot choices"
date: 2008-05-04
forum: General Help
---

### Post by jesse c on 2008-05-04
I have a question that is not a problem ,yet.When my boot screen shows at startup why do i have 6 choices of ubuntu to boot(3generic and 3recovery)?I normally just let it auto boot after its 15sec timer so it really doesnt affect me,but i know it used to have 4 now it has 6.I am in a dual boot install so i have the longhorn boot options after the 6 ubuntu options,but that shouldnt have anything to do with anything

---

### Post by Aearenda on 2008-05-04
Each time there is a new kernel update, you get a new pair of entries for a normal start and a recovery start. The older ones are kept so that you can drop back to the previous kernel if you find the new one breaks something on your system. You can press ENTER on that screen to speed things up - it will start the chosen entry. You can also shorten the timeout (I set it to 3 seconds) by doing this:
```
gksudo gedit /boot/grub/menu.lst
```
and then changing the value alongside 'timeout' (it's on line 19 in mine) to a suitable number, and saving the file. Take care not to alter anything else!

It definitely is a feature not a problem :-)

---

