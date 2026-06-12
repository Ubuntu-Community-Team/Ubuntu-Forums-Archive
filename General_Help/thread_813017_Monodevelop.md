---
title: "Monodevelop"
date: 2008-05-30
forum: General Help
---

### Post by Cr0m4T on 2008-05-30
I have problems compiling c and c++ programs in monodevelop.When i try to run(F5) i get this in the Build output:

Build failed. Object reference not set to an instance of an object

I checked under the preferences,my default c compiler is gcc and for c++ its g++.

Where is the problem?

---

### Post by WRDN on 2008-05-30
Could you post your source code, so it can be checked for errors.

Also, you could try compiling in the terminal. To do this:

cd to the directory.

```
cd [directory]
```

Type:

```
gmcs [filename]
```

This will create the executable from the .cs file.

Finally, type:

```
./[executable_name]
```

. . . to run the executable.

---

### Post by Cr0m4T on 2008-05-30
The source code is a simple Hello World (wrote one, and then copy-pasted one from the net), i installed monodevelop recently and
was trying to see how it works. C# is compiling and working normally. No problems with the terminal either.

---

### Post by Cr0m4T on 2008-05-30
No one had similiar problem?

---

### Post by Cr0m4T on 2008-05-30
Found the problem.:lolflag: Instead of New solution i went New File. Under new solution everything is working ok. But i still dont understand why i cant compile c or c++ code if u go New File?

WRDN thank you for ur time and help.

---

