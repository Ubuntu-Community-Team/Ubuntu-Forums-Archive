---
title: "Can't uncompress with Tar"
date: 2004-10-31
forum: General Help
---

### Post by Julius on 2004-10-31
I'm experiencing some problems with tar.
When I type, tar -xvfz file.tar.bz

It gives me this error:

$ tar -xvfz firefox-1.0rc1.es-ES.linux-i686.tar.gz
tar: z: No se puede open: No existe el fichero o el directorio
tar: El error no es recuperable: salida ahora

--
Translation: 
tar: z: Can't open (or cannot be opened). File or directory doesn't exist.
--

THe fact is that I know the file is there, and it's not mistyped (I always copy the file name in ls :P) 
I have reinstalled the tar package from the cd using synaptic but still doesn't work.

Could it be possible that some application has broken tar?

I have no problems at all uncompressing files .tar.bz2, just with tar.gz

:(

It was working fine until now.
PS: Uncompression works fine using nautilus.

---

### Post by filipe on 2004-10-31
Hi,

Assuming there are NO spaces in your filename, you have a strange problem there... :-k 
Try to solve it in two separate steps:

1) Uncompress first:

 ```
gunzip filename.tar.gz
```

2) and then untar the resulting file without the z option :

```
tar xvf filename.tar
```

This should work  ;)

---

### Post by ynef on 2004-10-31
What you did wrong was mess up the order of the options to tar -- the -f option is to be followed by the filename, but the way you wrote it, the filename doesn't get sent to tar at all (since the 'z' was following the f).

---

### Post by Julius on 2004-10-31
[QUOTE=filipe]Hi,

Assuming there are NO spaces in your filename, you have a strange problem there... :-k 
Try to solve it in two separate steps:

1) Uncompress first:

 ```
gunzip filename.tar.gz
```

2) and then untar the resulting file without the z option :

```
tar xvf filename.tar
```

This should work  ;)[/QUOTE]

---
THis works, thanks ;)

---

### Post by Julius on 2004-10-31
[QUOTE=ynef]What you did wrong was mess up the order of the options to tar -- the -f option is to be followed by the filename, but the way you wrote it, the filename doesn't get sent to tar at all (since the 'z' was following the f).[/QUOTE]


tar -xzvf file.tar.gz

That works too. It's strange, because I have been using "tar -xvfz" without problems.

ANyway, if this works, I don't care :)

Thanks!

---

