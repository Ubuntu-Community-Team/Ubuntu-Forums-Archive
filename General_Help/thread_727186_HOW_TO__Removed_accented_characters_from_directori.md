---
title: "HOW TO : Removed accented characters from directories and files"
date: 2008-03-17
forum: General Help
---

### Post by llebegue on 2008-03-17
Hi,

I was having problems whith file name containing accents in french. Here is the little bash script I wrote to convert these accents.
```

moved=0
#rename directories first
for dir in $(find . -type d | sort)
 do
	echo Processing $dir directory ..
	newname=$(unaccent UTF8 $dir)
	if [ "$newname" != "$dir" ]
	then
		if [ -d $dir ]
		then
			echo old name : $dir , new name : $newname
		fi
		if [ -d $newname ]
		then
			echo $newname already exist, copy content of $dir under $newname
			cp -R $dir/* $newname 2>/dev/null
			rm -fr $dir
			moved=$(expr $moved + 1)
		else
			# $dir coud have been moved in the meantime because of previous conditions
			if [ -d $dir ]
			then
				mv $dir $newname
			fi
		fi
	fi
	#rename files
	if [ -d $newname ]
	then
		cd $newname
		for file in *
		do
			if [ -e "$file" ]
			then
				newname=$(echo "$file" | tr ' ' '_' | unaccent UTF8 )
				if [ "$newname" != "$file" ]
				then
					if [ -e "$file" ]
					then
						echo old name : "$file", new name : "$newname"
						mv "$file" "$newname"
					fi
				fi
			fi
		done
		cd - >/dev/null
	else
		echo $newname not a directory ... check next
	fi

done
if [ $moved -ne 0 ]
then
	echo Number of directories moved : $moved, try again to remove accents.
fi


```

it requires to have the "unaccent" package installed

```

sudo apt-get install unaccent

```

---

