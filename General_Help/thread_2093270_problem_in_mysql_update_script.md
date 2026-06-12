---
title: "problem in mysql update script"
date: 2012-12-10
forum: General Help
---

### Post by alfa16vjtd on 2012-12-10
Dear all,

I'm trying to write a script who updates a database from data in a mail.
However it always skips one mail.

This is the script.

#!/bin/bash
fetchmail

while [ $? != 1 ]; do
{

mailx << EOF > /dev/shm/outfile
U
1
delete
q
EOF
if [ $? -eq 1 ]
then
tac /dev/shm/outfile > /dev/shm/outfile2
field1=`sed -n '2p' /dev/shm/outfile2`
echo $?
field2=`sed -n '3p' /dev/shm/outfile2`
echo $?
/usr/bin/mysql -h localhost -u user --password=pass <<EOF
use test;
UPDATE database set field1 = "$field1" where field2 = "$field2"
EOF

break
fi

tac /dev/shm/outfile > /dev/shm/outfile2
field1=`sed -n '3p' /dev/shm/outfile2`
echo $?
field2=`sed -n '4p' /dev/shm/outfile2`
echo $?
/usr/bin/mysql -h localhost -u user --password=pass <<EOF
use test;
UPDATE database set field1 = "$field1" where field2 = "$field2"
EOF
echo $?
} done

if I remove the complete if statement then everything works but the script stays in the loop.

thx in advance

---

