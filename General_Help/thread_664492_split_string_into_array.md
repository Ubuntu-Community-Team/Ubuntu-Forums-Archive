---
title: "split string into array"
date: 2008-01-11
forum: General Help
---

### Post by Tex-Twil on 2008-01-11
Hello,
I have a very basic question. In shell script,  how can I split a comma separated value into an array, each element of the array containing one value.

```

var="one,two,three,four"

# split into myArray

echo {myAray[@]}  # one two three four

```

thanks for your help.

---

### Post by lolindrath on 2008-01-11
Hello,

Here's a quick example I made, hopefully it helps: (I'm assuming you're using bash, btw)

[PHP]#declare your array
declare -a var

#split your line using tr
var=(`echo one,two,three,four | tr ',' ' '`)

#print the whole array
echo ${var[@]}

#iterate over the array
for s in ${var[@]}; do
	echo $s
done[/PHP]

---

### Post by ghostdog74 on 2008-01-11
```

# var="one,two,three,four"
# IFS=","
# set -- $var
# echo $1
one
# echo $2
two
# echo $3
three
# echo $4
four


```

---

### Post by dagnabit dang doohickey on 2008-01-11
```

foo="one,two,three,four"

IFS=","

bar=( $foo )

echo ${bar[0]}
echo ${bar[1]}
echo ${bar[2]}
echo ${bar[3]}

```

The above will output:
one
two
three
four

Sometimes you may want to add a couple of lines to the script to return IFS to it's previous value:
```

foo="one,two,three,four"

OLD_IFS="$IFS"
IFS=","

bar=( $foo )

IFS="$OLD_IFS"

echo ${bar[0]}
echo ${bar[1]}
echo ${bar[2]}
echo ${bar[3]}

```

---

