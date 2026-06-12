---
title: "Printing from Eclipse IDE"
date: 2005-07-03
forum: General Help
---

### Post by tman_ubuntu on 2005-07-03
I am unable to print from Eclipse IDE because the Print option is turned off.  How do I turn on the Print option in Eclipse or just plain print?

---

### Post by ninocass on 2005-12-05
ever get this sorted? im experiencing the same problem

---

### Post by monkiki on 2006-09-13
see  [http://www.eclipsezone.com/eclipse/forums/t76680.html](http://www.eclipsezone.com/eclipse/forums/t76680.html)
and [http://www.eclipse.org/swt/faq.php#printOnX](http://www.eclipse.org/swt/faq.php#printOnX)

---

### Post by andrew frank on 2007-04-09
i still have the same problem - "Print" is grayed out and i cannot print.
i run feisty 7.04! and i think all the gtk modules i have loaded are 2.10 -- so what am i missing?

any help is appreciated!
andrew

---

### Post by tagra123 on 2007-04-15
Anyone?

---

### Post by Kagee on 2007-06-27
Feisty delivers Eclipse 3.2.2, you need 3.3.x to print normally. (3.3 is only RC4 atm)

Alternative solution: 
[http://www.eclipse.org/swt/faq.php#printOnX](http://www.eclipse.org/swt/faq.php#printOnX)

> Q: How do I print using my favorite Unix print program?
    A: You can use the External Tools support in Eclipse to print files using external programs. Just create a new Program launch config from the External Tools dialog that launches your favorite printing utility and you can pass the selected resource as a parameter.

       1. Select the file you want to print.
       2. Run > External Tools > External Tools...
       3. Select "Program" in the Configurations: list.
       4. Click New
       5. Type: Print Selected File
          in the Name: field.
       6. Type the full path name of your favorite printing program in the Location: field. For example: /usr/bin/lpr
       7. Type: ${container_loc}/${resource_name}
          in the Arguments: field.
       8. Click Apply
       9. Click Run

Maybe because i use 3 printers, i had to use: 
-PTreekiller ${container_loc}/${resource_name}
in the Arguments: field (Treekiller is the name of my only real printer)

I later added a second external program with the arguments
-PPDFPrint ${container_loc}/${resource_name}

---

### Post by snarve on 2007-10-20
Thanks. That worked.

---

