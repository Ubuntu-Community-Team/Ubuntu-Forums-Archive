---
title: "Can't find MusiXTex"
date: 2006-12-08
forum: General Help
---

### Post by jfbailey on 2006-12-08
Hello,

According to my Ubuntu's Synaptic Package Manager, Musixtex, pmx, m-tex and roseblossom music scoring programs are installed on my computer. Problem is, I can't find them in the a la carte menu or in the debian menu, nor can I activate them through any of the several suggestions for using the console or the terminal. 

Typing "musixtex" into the terminal gets me the following:

"This script automates the three-pass TeX compilation of MusiXTeX music score files. Note: this script nay not work for certain files. You ay run tex/latex and musixflx manually in such cases. Usage: musixtex file.tex (TeX options)"

Thanks for any help you can provide, but please be warned that I'm likely not to be able to understand any but the most idiot-proof explanations. 

Thanks again! 

Joe

---

### Post by bodhi.zazen on 2006-12-08
Sometimes I find I need to log out and back in for the menu to be updated.

You can find the program:```
which musixtex
```

And add a launcher or menu item, put the path (returned with whereis) in the "command" box.

Or do you need help with usage.

Looks like the command should be

musixtex <insert_file_name_here> <Options here, if any>

also try man musixtex

---

