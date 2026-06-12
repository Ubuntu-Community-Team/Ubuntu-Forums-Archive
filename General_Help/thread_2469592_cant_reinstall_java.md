---
title: "cant reinstall java"
date: 2021-12-03
forum: General Help
---

### Post by jagarciasa302 on 2021-12-03
Hello everybody
 I&#8217;m new in linux so I&#8217;m having a lot of problems
 yesterday I had problems with java so I remove it since then i&#8217;ve beeing traying to reinstall it but I cant
 this message appears every time I chech java version
 I type java &#8211;version
 and then it says
 
 
 No se ha encontrado la orden «java», pero se puede instalar con:
 
 
 ```
sudo apt install default-jre              # version 2:1.11-72, or
 sudo apt install openjdk-11-jre-headless  # version 11.0.11+9-0ubuntu2~20.04
 sudo apt install openjdk-13-jre-headless  # version 13.0.7+5-0ubuntu1~20.04
 sudo apt install openjdk-16-jre-headless  # version 16.0.1+9-1~20.04
 sudo apt install openjdk-17-jre-headless  # version 17+35-1~20.04
 sudo apt install openjdk-8-jre-headless   # version 8u292-b10-0ubuntu1~20.04
```
 
 
 if I tried again to uso the comand sudo apt install default-jre the same message appears again
 
 
 Can anybody help me please, I&#8217;ll send all the info you need if I&#8217;m able to do it
 
 
 Sorry if this is not the place for posting this doubt

---

### Post by saamaan on 2021-12-03
Same proble here.

---

### Post by dragonfly41 on 2021-12-03
Might try running Synaptic Package Manager to install packages.

Just search "openjdk" .. select package(s) and apply.

---

### Post by jagarciasa302 on 2021-12-04
it didnt work :(

---

### Post by dragonfly41 on 2021-12-04
> [COLOR=#000000]it didnt work[/COLOR]

Please be more specific.
Did you "see" any openjdk entries in Synaptic Package Manager?
Explain the steps you took.

---

### Post by jagarciasa302 on 2021-12-05
Firstable I've realized sth might be important: a couple of days ago I changed JAVA_HOME path, like I read in the spanish gobernement&#8217;s guide for installing a website signer
[I]
Configurar la variable JAVA_HOME con la JRE instalada y su directorio &#8220;bin&#8221; como parte del 
PATH del sistema. Esto se puede hacer, por ejemplo, editando el fichero &#8220;/etc/environment&#8221; y 
agregando a la variable PATH la ruta del directorio bin de Java y la nueva variable:  

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/
games:/usr/local/games:/usr/java/jre1.8.0_121/bin" 
JAVA_HOME="/usr/java/jre1.8.0_121"  

 
Podemos hacer que el sistema recargue la configuración de este fichero (y así no sea necesario 
reiniciarlo) con el comando: 
source /etc/environment[/I]
(I can traslate it if you cant understand it)

What I did about what you told me was:  I run Snynaptic Package Manager, in the browser I typed "openjdk", I selected "default-jdk" packaged (automaticly "default-jdk-headless&#8221;, &#8220;default-jre&#8221; and "default-jre-headless" were selected" I press Apply and it were installed.
Then I typed the comand "java --version" and I had the same message:
"java comand was not found"

---

### Post by dragonfly41 on 2021-12-05
I prefer to set env variables in $HOME/.profile  (hidden file).

See this old thread .. (7 years old).

[https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables)

Here is my own Java entry (after installing Java through Synaptic Package Manager or other methods).

```

export JAVA_HOME="/usr/lib/jvm/java-14-openjdk-amd64"
export JAVA_INCLUDE_DIR="/usr/lib/jvm/java-14-openjdk-amd64/include"
export JAVA_OPTIONS=Xmx512M

```

If you are developing in Java I suggest that you install IntelliJ IDEA community version.

[https://www.jetbrains.com/idea/](https://www.jetbrains.com/idea/)

I have added a screenshot of my Synaptic Package Manager view of “openjdk” packages.

I use DeepL for translation of text snippets.


[https://www.deepl.com/translator#es/en/](https://www.deepl.com/translator#es/en/)

---

