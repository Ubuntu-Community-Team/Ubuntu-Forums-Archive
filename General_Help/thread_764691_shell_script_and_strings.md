---
title: "shell script and strings"
date: 2008-04-24
forum: General Help
---

### Post by big136 on 2008-04-24
Hi,
1- where can I post the questions in shell scripting under UBUNTU ?
2- if here :
I should read a number situated just after "= " symbole in a line from a file and put it in a variable.
the line in file is :
number of transaction=7

and I should put 7 in a variable (7 or other values), then 
read the file :


And then how to select just the number after = symbole :

myvariable2=????

Thanks for help.

---

### Post by justleen on 2008-04-24
you could use awk, with a custom field seperator:
```

VAR=`echo 'this is a test=9'| awk -F '=' '{print $2}'`

echo $VAR

```

or you could use sed, deleting everything up to the = sign

```

echo 'this is a test string=9'|sed 's/.*.=//'

```

---

### Post by big136 on 2008-04-24
Thank you.

---

### Post by big136 on 2008-04-24
Hi,
thanks for your help. using your guidlines I wrote this script :
# ! /bin/sh
file=snapshot.txt
cat $file | while read line ;
do
{
myvariable=`grep "Nombre de ROLLBACK internes"  |sed 's/.*.=//'`
echo $myvariable
}
done

It looks in a file "snapshot.txt" for the lines containing "Nombre de ROLLBACK internes". But there are two lines containing this :
Nombre de ROLLBACK internes                       = 0
Nombre de ROLLBACK internes dus à interblocages   = 7
1-How can I exclude the following 
Nombre de ROLLBACK internes dus à interblocages   = 7
2- at present the echo $myvariable displays :
0 7
how can I have :
0
7

Many thanks.

---

### Post by bingoUV on 2008-04-24
```

file=snapshot.txt
for i in `cat $file| grep -v ' Nombre de ROLLBACK internes dus à interblocages' | sed 's/.*.=//'`; do
    echo $i;
done

```

EDIT : 
```

cat $file| grep -v ' Nombre de ROLLBACK internes dus à interblocages' | sed 's/.*.=//' 

```is enough for what you are doing. Wrote the script just in case it is necessary to take values in some variable to do some further processing.

---

### Post by big136 on 2008-04-24
Thank you.
But applying the following :
```

file=snapshot.txt
for i in `cat $file| grep -v ' Nombre de ROLLBACK internes dus à interblocages' | sed 's/.*.=//'`; do
    echo $i;
done

```
we will exclude only following :
".....Nombre de ROLLBACK internes dus à....."
but there are some other lines with "=" symbol. They would be captured.
```

Num. de partition de base de données du catalogue       = 0
Nom du catalogue du noeud réseau                        =
Syst. d'exploitation serveur de base de données         = NT
Emplacement de la base de données                       = Local
Horodatage de la première connexion à la base     = 18.04.2008 05:31:56.832765

```
Regards.

---

### Post by bingoUV on 2008-04-24
so add grep clauses for those strings that you want to include. I don't know about which strings you want and which you do not want.

---

### Post by bingoUV on 2008-04-24
deleted duplicate post

---

