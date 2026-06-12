---
title: "problems with MonoDevelop"
date: 2007-10-03
forum: General Help
---

### Post by dany_tab on 2007-10-03
hey. i am programming in C# on UBUNTU monodevelop. and when i write the next 
```
// project created on 9/6/2007 at 9:16 PM
using System;

namespace dany
{
class MainClass
{
 public static void Main(string[] args)
 {
  int num;
  num=int.Parse( Console.ReadLine());
  Console.WriteLine(num);
 }
}
}
```

and when i compile it i get the next output:

[IMG]http://www.israel-forum.co.il/forums/index.php?act=Attach&type=post&id=54869[/IMG]

this code compiles good in visual studio 2005.

why it doesnt work? 

help please

---

### Post by Lord Illidan on 2007-10-03
The code is good. The problem is that the terminal inbuilt into monodevelop doesn't support input. So, what you have to do is open up a terminal, navigate to the directory where you're storing your program, then go to the bin/debug directory, and you'll find a file called xxxx.exe. Then type mono xxxx.exe in that directory to run the program.

---

### Post by dany_tab on 2007-10-03
thanks. :)
i solved it the next way:
i entered:
Project-->Options
and then
Configuration-->Debug-->Output
and marked:
Run on external console

and it works:):)

---

### Post by Lord Illidan on 2007-10-03
I love you! That's the thing I've been looking for..

---

