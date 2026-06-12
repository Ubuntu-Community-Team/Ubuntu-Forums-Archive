---
title: "Bash script help"
date: 2017-06-19
forum: General Help
---

### Post by YaPaY on 2017-06-19
[PHP]for i in 11 71 16 17 21 26 28 42 43 26 19 2 22 3 25 64 69 58
do
URL="http://127.0.0.1:8000/live/admin/12drf2vjVOm/$i.ts"

HAS_AAC_OUT=$(ffmpeg -i $URL 2>&1 | grep 48000)
if [ -z "$HAS_AAC_OUT" ];then
  FILE=${URL##*/}
if
  echo "ERRORTS=${FILE%.*}"

exit 1
else
echo "$i"

fi
done
exit 0
[/PHP]

I would like to see the assigned variable instead of i value. For example 11=ATA 17=CCC etc

How can use if like this:

if i=11  then
echo "ERRORTS=ATA"

if i=17  then
echo "ERRORTS=CCC"

the current script gives me the i value if the stream has no parameter as AAC

ERRORTS=11

I have to check 11 every time for real value. If I owuld do that I won't have to check.

many thanks in advance

---

### Post by SeijiSensei on 2017-06-19
You could try using the "case" construct in bash:
```

case "$i" in
   ATA)
   do stuff
   ;;

   CCC)
   do other stuff
   ;;

   *)
   throw error?
   ;;
esac

```

---

### Post by YaPaY on 2017-06-19
thanks but I am not a programmer :(

---

