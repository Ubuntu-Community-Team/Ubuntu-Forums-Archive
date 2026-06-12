---
title: "Compiling latest version of Kazehakase"
date: 2007-03-07
forum: General Help
---

### Post by raul_ on 2007-03-07
> **zarathustra said:**
> I compiled version 0.4.4.1 fine on Edgy, supposedly this had compile error fixes. Have you tried compiling this version?

Weirdly enough i compiled it, removed it, tried to compile it again, and now it doesn.t work. Something about "permission denied" even with root

I suppose some package is missing, but i don't have any leads

EDIT: Here is the error:

```
 make
make  all-recursive
make[1]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
Making all in po
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
Making all in src
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
(echo "#include \"kz-marshalers.h\""; \
           ../src/kz-marshalers.list --body --prefix=_kz_marshal) > kz-marshalers.c
/bin/bash: line 1: ../src/kz-marshalers.list: Permissão negada
make[2]: ** [kz-marshalers.c] Erro 126
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
make: ** [all] Erro 2

```

Permission denied...

---

### Post by hanzomon4 on 2007-03-07
I compiled  v0.4.4.1 and I like it I noticed that some things don't render correctly like the search triangle toggle on these forums. I also don't know how to get the [thumbnails-preview]("http://i.iinfo.cz/urs/Kaz04-112349053355064.png") in the sidebar, but I like it for the most part....

---

### Post by zarathustra on 2007-03-08
> **raul_ said:**
> Weirdly enough i compiled it, removed it, tried to compile it again, and now it doesn.t work. Something about "permission denied" even with root

I suppose some package is missing, but i don't have any leads

EDIT: Here is the error:

```
 make
make  all-recursive
make[1]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
Making all in po
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
make[2]: Nada a ser feito para `all'.
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/po'
Making all in src
make[2]: Entrando no diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
(echo "#include \"kz-marshalers.h\""; \
           ../src/kz-marshalers.list --body --prefix=_kz_marshal) > kz-marshalers.c
/bin/bash: line 1: ../src/kz-marshalers.list: Permissão negada
make[2]: ** [kz-marshalers.c] Erro 126
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
make: ** [all] Erro 2

```

Permission denied...

That's strange, have you checked you have permission for all the files in the source directory?

---

### Post by raul_ on 2007-03-08
> **zarathustra said:**
> That's strange, have you checked you have permission for all the files in the source directory?

Yeap, check out this thread

[http://www.ubuntuforums.org/showthread.php?t=375802]("http://www.ubuntuforums.org/showthread.php?t=375802")

---

### Post by zarathustra on 2007-03-08
> **raul_ said:**
> Yeap, check out this thread

[http://www.ubuntuforums.org/showthread.php?t=375802]("http://www.ubuntuforums.org/showthread.php?t=375802")

Try doing the same thing again but with -R added after chmod. I think it's only changing the permissions of the actual folder, not its contents.

---

### Post by raul_ on 2007-03-08
But the error now is 

```
/bin/bash: line 6: --fhead: comando não encontrado
make[2]: ** [stamp-kz-enum-types-c] Erro 127
make[2]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1/src'
make[1]: ** [all-recursive] Erro 1
make[1]: Saindo do diretório `/home/raul/Desktop/kazehakase-0.4.4.1'
make: ** [all] Erro 2
```

--fhead: command not found

---

### Post by Brunellus on 2007-03-08
I'm going to split the technical problems off into their own thread, and move them to a relevant technical sub-forum.

---

### Post by zarathustra on 2007-03-08
Have you tried doing make clean then configure and make again? Can you post a bit more of the compilation just before the error? I'm just guessing as to what the problem is (something I often have to do when my compiling doesn't work!)

---

