---
title: "A bash script to bulk rename files from numeric to alphabetical order?"
date: 2023-01-21
forum: General Help
---

### Post by DVD-R on 2023-01-21
Hello all,
I'm wondering if anyone knows of a working Bash script for renaming files in their proper numeric order

For example:

from:
0001.txt 
0002.txt
0003.txt

to:
AAA.txt
AAB.txt
AAC.txt

The key to this would be - the script would have to be able to read the input filenames by their numeric values rather than by their alphabetical values.
If the script reads the input files in the alpha order - it will re-sort them in that order - and the correct sequential order of the files will be lost.

Wondering if anyone has done this?
Sincere thanks in advance

---

### Post by #&amp;thj^% on 2023-01-21
maybe this, 

If all files are in the same directory the sequence

```
ls | 
sed -n 's/\(.*\)\(-[0-9.]*\.pkg\)/mv "\1\2" "\1.pkg"/p' | 
sh
```
BTW I've not used that for few years now in XFCE I had a Bluk-renamer, (I've been spoiled with that tool)

---

### Post by DVD-R on 2023-01-21
Thanks!
I'll try this!  :-]

Much appreciate!!

---

### Post by DVD-R on 2023-01-21
Well - I was unable to get it to work.

I assumed the extension of the file in the example - was pkg 
So I changed that to txt

ls | 
sed -n 's/\(.*\)\(-[0-9.]*\.txt\)/mv "\1\2" "\1.txt"/p' | 
sh

But it did not rename the files.
So it appears it did not identify .txt files within the folder.

---

### Post by MAFoElffen on 2023-01-22
So... Solve the riddle.

The basic Logical Flow of something like that is to translate base 10 to base 26, A_Z being 1-26... so that AAA means 1 and is always translated from 0001, and ABA means 27 and it translates to 00027... See where that goes? and vice versa. In Bash, setting up an Alpha Character Set to have a numeric value... Then the algorithm of that would need to do the mapping of that numeric back to a string in the rename process.

In the set:
AAA=1, AAB=2, AAC=3..., AAZ=26... ABA=27... and so on. Creating a set with a numeric value tranlsation. Would be a lot in BASH to write that out, but a lot simpler in Python, where you can easily get a numeric value for an alpha letter

Something like:

In a one liner-
```

print [ord(char) - 96 for char in raw_input('Write Text: ').lower()]

```
OR

Writen out-
```

input = raw_input('Write Text: ')
input = input.lower()
output = []
for character in input:
    number = ord(character) - 96
    output.append(number)
print output

```
but then add the digits in Base 26...

Something like that? Just thinking out loud...

---

### Post by #&amp;thj^% on 2023-01-22
+1 ^^^^^
as I said it's been a while since i used my script, I think I left out a second part to it, I used it to rename my back-up's years ago
I like what MAFoElffen offered better.
Sorry i wasn't paying attention yesterday.

---

### Post by MAFoElffen on 2023-01-22
If in BASH, you can see by this example, that it could get long very fast
```

translation_table={
  '0001'='AAA', '0002'='AAB', '0003'='AAB', '0004'='AAC', '0005'='AAE', '0006'='AAF',
  '0007'='AAG', '0008'='AAH', '0009'='AAI', '0010'='AAJ', '0011'='AAK', '0012'='AAL',
  '0013'='AAM', '0014'='AAN', '0015'='AAO', '0016'='AAP', '0017'='AAQ', '0018'='AAR',
  '0019'='AAS', '0020'='AAT', '0021'='AAU', '0022'='AAV', '0023'='AAW', '0024'='AAX',
  '0025'='AAY', '0026'='AAZ',
  '0027'='ABA', '0028'='ABB', '0029'='ABB', '0030'='ABC', '0031'='ABE', '0032'='ABF',
  '0033'='ABG', '0034'='ABH', '0035'='ABI', '0036'='ABJ', '0037'='ABK', '0038'='ABL',
  '0039'='ABM', '0040'='AAN', '0044'='ABO', '0045'='ABP', '0046'='ABQ', '0047'='ABR',
  '0048'='ABR', '0049'='ABS', '0050'='ABT', '0051'='ABU', '0052'='ABV', '0053'='ABW',
  '0054'='ABX', '0055'='ABY',
  '0056'='ACA', '0057'='ACB', '0058'='ACB', '0059'='ACC', '0060'='ACE', '0061'='ACF',
  '0062'='ACG', '0063'='ACH', '0064'='ACI', '0065'='ACJ', '0066'='ACK', '0067'='ACL',
  '0068'='ACM', '0069'='ACN', '0070'='ACO', '0071'='ACP', '0072'='ACQ', '0073'='ACR',
  '0074'='ACS', '0075'='ACT', '0076'='ACU', '0077'='ACV', '0078'='ACW', '0079'='ACX',
  '0080'='ACY', '0081'='ACZ',
  ## AND ON AND SO FORTH...
             }

```
You can see that if done in BASH, if would be some work... 

But in BASH, if you converted the in numbers and translated the base in something like
```

#!/bin/bash
FileDirectory="/path/to"
# Index of this array is 0 through 25...
TransList={'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U'. 'V', 'W', 'X', 'Y', 'Z'}
# This builds the filelist
FileList=$(ls $FileDirectory | sort)

x=1 # decimal
i=0# valid range of i is 0-25
base26=

for file in ${FileList[@]}
do
  NewFileName=""
  file_eval=$(sed 's/\.txt//g') # This strips off the ".txt" off the filename
  # This converts base 10 to base 26 
  init_lookup=$( echo 'ibase=10; obase=26; $file_eval' | bc )
  echo $init_lookup # DEBUG statement
  # for $file_eval="0001" this evals to 01, which ${TransList[01]} should return "A"
  for digit in ${init_lookpup}
  do
    NewFileName=$NewFileName+${Tranlist[$digit]}
  done
  echo -e "$NewFileName.txt"
  # For "0027", this relates to "01 01", which should return "AA", so AA.txt
done

```
Something like that is a good start...

---

### Post by Holger_Gehrke on 2023-01-22
Actually it isn't all that complicated in bash either. You just use an array 
```
declare -a conv=({A..Z})
```
This creates an array with conv[0]='A' to conv[25]='Z'. Of course this means that AAA equals 0, not 1 ...
The complete conversion would look something like this:
```

#!/usr/bin/env bash
declare -a conv=({A..Z})
declare -i num
for i in *.txt; do
  # Force decimal by putting 10# before the number; otherwise names starting with '0' will get seen as octal.
  num=10#$(basename --suffix=.txt $i)
  # 26^3 is 17576; we're only expecting four decimal digits, so we are only doing three letters
  remainder=$((num%26))
  tgt=${conv[$remainder]}
  num=$((num/26))
  remainder=$((num%26))
  tgt=${conv[$remainder]}$tgt
  num=$((num/26))
  remainder=$((num%26))
  tgt=${conv[$remainder]}$tgt
  num=$((num/26))
  echo mv $i ${tgt}.txt
done

```

There are probably problems with this code (which is why I'm only echoing the mv-commands and not executing them ...).

Holger

---

### Post by MAFoElffen on 2023-01-23
I used Holger's array declare statement. I liked his shortcut on that... Tweaked my code, debugged, tested, and it works... LOL
```

#!/bin/bash
FileDirectory="./TestDirectory" # Change to the path of directory
# Index of this array is 0 through 25...
declare -a TransList=({A..Z}) # This builds the letter lookup table
FileList=$(ls $FileDirectory | sort) # Builds an array from listing the filenames of the directory

ConversionValue=702  # shift, starts it at "AAA"

for file in ${FileList[@]}
do
    NewFileName=""
    FValue=$(echo $file | \
        sed 's/\.txt//g') # This strips off the ".txt" off the filename
    Value=$(($ConversionValue+$FValue)) # This shifts the conversion for 001=AAA, staring with AAA
    # This converts the base from 10 (decimal) to base 26 
    init_string=$( echo "ibase=10; obase=26; $Value" | bc ) # This outputs as string
    
    IFS=' ' read -r -a init_array <<< "$init_string" # Convert the string to an array

    for digit in ${init_array[@]}
    do
        digit=$(($digit-1)) # Adjust for correct index in Letter Lookup Table
        Translation=${TransList[$digit]}
        NewFileName="$NewFileName$Translation"
    done

    mv $FileDirectory$file $FileDirectory/$NewFileName.txt # Rename the file
done
echo 'Done...'

```

---

### Post by Holger_Gehrke on 2023-01-23
@MAFoElffen: a few more tweaks for you ...

line 5: never ever use ls to generate lists of files. The output of ls is meant for human consumption and theoretically subject to change without notice.
```

FileList=(${FileDirectory}/*) # could even use '/*.txt' in case there are other kinds of files in there

```
The pipe into 'sort' is not necessary, the list gets sorted by the shell anyway. And who actually cares about the order as long as everything is in there ...

The elements of FileList will have a path and an extension which will need to be removed. But sending them through 'sed' is a bit of overkill, there are parameter expansions for removing prefixes or postfixes from strings.
So lines 12 and 13 should be
```

  FValue=${file%.*} #cut off the extension (shortest match for .*)
  FValue=${FValue##*/} # cut off the path (longest match for */)

```
Using basically the same trick as for the translation array, we can shorten the generation of init_array into one line
```

  init_array=( $(echo "ibase=10; obase=26; $Value"|bc) ) # the output of bc are groups of two digits separated by space; exactly what the shell expects for filling an array

```

These changes gets rid of a lot of calls to external programs and should be both a bit faster and more readable (for someone familiar with the shell).

Holger

---

### Post by MAFoElffen on 2023-01-23
Thank you for the pointers... sed for me is like from my mainframe days, when a mainframe binary sort to get extracts of data to (re)define in the database was the fastest and less CPU (more efficient way) to do ADHOC Reporting...

The specific sort left on the directory listing was when I had some other logic going through my head... LOL. Was still working out the logic. It is a good "riddle'. LOL

Incorporating both would give the OP:
```

#!/bin/bash
## MAFoElffen, 2022.01.21
## Contributor: Holger_Gehrke 2022.01.22
# ScriptName: MassRename

FileDirectory="./TestDirectory" # Change this value to the path of the files directory
# Index of this array is 0 through 25...
declare -a TransList=({A..Z}) # This builds the letter lookup table
FileList=(${FileDirectory}/*.txt) # Builds an array from listing the filenames of the directory

ConversionValue=702  # shift, starts it at "AAA"

for file in ${FileList[@]}
do
    NewFileName=""
    FValue=${file%.*} #cut off the extension (shortest match for .*)
    FValue=${FValue##*/} # cut off the path (longest match for */)
    Value=$(($ConversionValue+$FValue)) # This shifts the conversion for 001=AAA, staring with AAA
    # This converts the base from 10 (decimal) to base 26 
    init_array=( $(echo "ibase=10; obase=26; $Value"|bc) ) # the output of bc are groups of two digits separated by space

    for digit in ${init_array[@]}
    do
        digit=$(($digit-1)) # Adjust for correct index in Letter Lookup Table
        Translation=${TransList[$digit]}
        NewFileName="$NewFileName$Translation"
    done

    mv $FileDirectory$file $FileDirectory/$NewFileName.txt # Rename the file
done
echo 'Done...'

```

---

### Post by #&amp;thj^% on 2023-01-23
I'm just going to set back and enjoy the solving of this riddle...:P
This has been both fun and educational to watch..

---

### Post by TheFu on 2023-01-23
Sometimes using 'qmv' is easier.  Then you can use the power of your editor to handle sequences in a more visual way.
Just another option to consider.

In vim, 'g<cntl>a' will increment numbers that are in a column selection.  To make it increment letters, set the nrformat to include alpha, then do the same selection, and g<cntl>a will create:
```
a
b
c
d
e
f
g
h
i
j
k
```

Unfortunately, the 
```
aa
aa
aa
aa
aa
```
becomes
```
ba
ca
da
ea
fa
```

Anyway, 50 solutions to this issue.  At least with qmv, we have an editor where the new names are easily seen and whatever editor you prefer can be leveraged. If vim is your editor [https://www.youtube.com/watch?v=sQA63cI1khU](https://www.youtube.com/watch?v=sQA63cI1khU) shows how to use q+<cntl>a in a few minutes.  qmv is a great tool.

It is also possible to use a spreadsheet ... pull in the list of files, create a spreadsheet function to make the next cell over have the new name that is desired, then export that sheet as a text file, add "mv" to the beginning of each line, then run the script.  I write scripts to create other scripts all the time.

After all, we just want something like this to be created:
```
mv 0001.txt AAA.txt
mv 0002.txt AAB.txt
mv 0003.txt AAC.txt
```

If we don't care about the input filename and output filenames being connected in any way at all, Then a simple bash sequence can be used 
```
for I in {A..Z} ; do echo $I;  done
```

Make that nested to get 3 characters:
```
 for I1 in {A..Z} ; do
  for I2 in {A..Z} ; do
    for I3 in {A..Z} ; do

      echo $I1$I2$I3

    done
  done
done

```

Output is:
```

AAA
AAB
...
ZZY
ZZZ

```

Easy.

---

