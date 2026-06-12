---
title: "can i use awk to do this instad of a for do read loop?"
date: 2013-09-27
forum: General Help
---

### Post by David_Field on 2013-09-27
I have a script which is using hashdeep to generat sha256 and md5 hashes on files on my linux distro and piping them to a file
the file is over 310000 lines long

im then using a script function to seperate each line, and cut to split the data in each line

```
while read p; do  echo "This is a line im reading $p"
  size=$(echo $p | cut -d, -f 1)
  md5=$(echo $p | cut -d, -f 2 | cut -d ' ' -f 1)
  sha256=$(echo $p | cut -d, -f 3 | cut -d ' ' -f 2)
  filename=$(echo $p | cut -d, -f 4 | cut -d ' ' -f 3)
	##devugging
	echo "Filesize: $size"
	echo "MD5: $md5"
	echo "SHA: $sha256"
	echo "Filename: $filename"
	echo "-----------------------------"
mysql --host=$sqlhost --user=$sqluser --password=$sqlpass $sqldb << EOF
insert into $sqltable3 (size,md5,sha256,filename) values('$size','$md5','$sha266','$filename');
EOF
done < $md5pre



```

Its taking over a day to import, i've read that its mybe possible to use awk to process and import this data into mysql far quicker than a line by line loop..

Can anyone point me in the right direction?

---

### Post by steeldriver on 2013-09-27
If the hashdeep command produces a comma separated file, it will probably be most efficient to do a mysql bulk insert ('LOAD DATA INFILE')

[http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html](http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html)

[http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html](http://dev.mysql.com/doc/refman/5.1/en/mysqlimport.html)

However if you really want to do it with a shell script loop, you don't need to do all those 'echo'es and 'cuts' - you can read multiple comma-limited variables either using

```

$ echo -e "a,b,c,d\ne,f,g,h" | while IFS="," read -r var0 var1 var2 var3; do echo "$var0" "$var3"; done
a d
e h

```

or into an array

```

$ echo -e "a,b,c,d\ne,f,g,h" | while IFS="," read -ra vars; do echo "${vars[0]}" "${vars[3]}"; done
a d
e h

```

---

### Post by markbl on 2013-09-28
I've written shell and awk scripts for over 23 years but nowadays we would do all that in python (or perl or ruby if they float your boat). I.e traverse and read the files, generate the hashes, sort/split, and write to sql, all in one python program.

---

### Post by info6 on 2013-11-14
I am having the dickens getting while loops to work in awk.  Here is the complete contents of a executable bash file

awk ' i=1
 while i<20 ; print i ; i+=2

When I run this file I get
awk: line 2: syntax error at or near while

I remember figuring this out in the 90's and it was something simple and stupid but heck I can't remember.
Can anyone tell me what I am doing wrong?

Inside my awk program I am trying to


  while FirstPass=="YES" {
#
# Build Header File
#
  print ( $0 ) >> /tmp/MP-Header ;
  getline ;
  /\<movielist\>/ FirstPass = "NO" ;
#
  }

I have used do/done do while and cannot get anything to not give an error.
Thanks for your help

---

