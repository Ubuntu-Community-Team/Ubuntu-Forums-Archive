---
title: "i can't run the update-manager"
date: 2007-02-14
forum: General Help
---

### Post by JCamus on 2007-02-14
that's just it... i try to run it in a terminal and i get this error:

```
bash: /usr/bin/update-manager: /usr/bin/python: intérprete incorrecto: Input/output error
```

i can still run synaptic thou. but when i try to update the "update-manager" (trying to fix it) it fails it says:

```
E: update-manager: el subproceso post-installation script devolvió el código de salida de error 2
```

in a terminal: 

```
/var/lib/dpkg/info/update-manager.postinst: 31: gconf-schemas: Input/output error
dpkg: error al procesar update-manager (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 update-manager

```

the thing is, i can't update anything. do you need any extra info so i get a little help? i'm on edgy eft and have enough to run it.
i'm kind of a n00b in linux but i'm willing to learn. and i searched the forum for anything that might be useful in order to resolve this issue, but i didn't run into anything like that. first timer in this forum, also.

so, help me, willya, please? :) 

ps: yes, i'm not using an english ubuntu version, i'm from chile. and my english sucks.

---

### Post by gradedcheese on 2007-02-15
update-manager is written in python.  Try running "python" from a terminal -- what errors (if any) do you get?

also, from a terminal you can run "sudo apt-get upgrade" to install all updates if you wish.

---

### Post by JCamus on 2007-02-15
well, when i try to run python from a terminal the error is that there's no command named python:
```
bash: python: orden no encontrada
```
and, when i use "sudo apt-get upgrade" to get updates, there are a lot of Input/output errors; something like this:
```
Preparando para reemplazar language-pack-es 1:6.10+20070115~prop1 (usando .../language-pack-es_1%3a6.10+20070115_all.deb) ...
Desempaquetando el reemplazo de language-pack-es ...
dpkg: error al procesar /var/cache/apt/archives/language-pack-es_1%3a6.10+20070115_all.deb (--unpack):
 no se puede efectuar `stat' sobre `./usr/share/locale-langpack/es/LC_MESSAGES/coreutils.mo' (que es lo que se iba a instalar): Input/output error
```

if you need me to (try to) translate something, just ask (and i'll try :P)

thanks in advance.

---

### Post by gradedcheese on 2007-02-15
thats ok, I speak Spanish.  It looks like there's a missing file that's causing it to fail when trying to upgrade "language-pack-es".  Please try this:

```

sudo apt-get remove language-pack-es
sudo apt-get install language-pack-es

```

Hopefully that will install it fresh (using the latest version).  Then try the "sudo apt-get update" when the error is resolved.

---

### Post by JCamus on 2007-02-15
ok, after the removal it continued with errors, regarding the update-manager: 
```
/var/lib/dpkg/info/update-manager.postinst: 31: gconf-schemas: Input/output error
dpkg: error processing update-manager (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
the same error showed up prior the instalation of the langpack.

i had the same error (langpack's missing file) with beryl, so i tried to remove it in order to repair it. but when it came to remove the dependencies it said:
```
Desinstalando beryl-settings-bindings ...
/var/lib/dpkg/info/beryl-settings-bindings.prerm: 6: update-python-modules: Input/output error
dpkg: error al procesar beryl-settings-bindings (--remove):
 el subproceso pre-removal script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 beryl-settings-bindings
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
so, it refuses to uninstall. when i do the upgrade, the only pack to do so is this one: beryl-settings-bindings. but it fails to upgrade and to remove. so i guess it's stuck.

well, the update-manager still doesn't work. it keeps showing the same error even after a few reboots. do you recomend anything else? these input/output errors are somewhat weird; everything written in python is just not working, i tried some more apps and they return an i/o error as well as update-manager, but without error dialog.

i thank you a lot for this far and for what i hope is coming.

---

### Post by gradedcheese on 2007-02-15
hmm... this is indeed rather odd.  First, python should be installed ("sudo apt-get install python"), however it really should have been there already, which is strange.  You could try reinstalling update-manager via apt-get, perhaps it will then replace whatever files are missing or otherwise repair its python dependencies.  So, as a first step: can you get python working?  "which python" should return "/usr/bin/python"

---

### Post by JCamus on 2007-02-15
wich python returns nothing, not even an error. 
trying to install python returns the error about the unremovable dependencies from beryl and the input/output error about the update-manager.

do you know how can i get rid of that dependency that is giving me this error? it was easy with the langpack. even when i disable the beryl repo it keeps saying that it *will* be actualised/removed.

then i run the upgrade and the error about the update-manager goes like this:

```
~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados. *--> this is the beryl dep, i think*
Necesito descargar 0B de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? S
Configurando update-manager (0.45.1) ...
***
* Updating MIME database in /usr/share/mime...
Wrote 485 strings at 20 - 2868
Wrote aliases at 2868 - 2a1c
Wrote parents at 2a1c - 341c
Wrote literal globs at 341c - 3480
Wrote suffix globs at 3480 - 68c8
Wrote full globs at 68c8 - 68ec
Wrote magic at 68ec - c050
Wrote namespace list at c050 - c060
***
/var/lib/dpkg/info/update-manager.postinst: 31: gconf-schemas: not found
dpkg: error al procesar update-manager (--configure):
 el subproceso post-installation script devolvió el código de salida de error 127
Se encontraron errores al procesar:
 update-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

edit: trying to run the update-manager from terminal gives me this now:
```
bash: /usr/bin/update-manager: /usr/bin/python: intérprete incorrecto: No existe el fichero ó directorio
```
wich annoys me, because i never touched python.

---

### Post by gradedcheese on 2007-02-16
hmm!  I really want to get this fixed for you, but it's a strange situation.  Mainly, we need to get python working on your system.

1) does python exist ("which python")
2) can you reinstall/configure it? (try "sudo apt-get install python" or "sudo dpkg --reconfigure python")
3) see if we can get more info on the broken dependencies ("sudo apt-get check")

---

