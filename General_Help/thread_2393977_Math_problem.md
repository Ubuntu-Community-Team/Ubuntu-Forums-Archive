---
title: "Math problem"
date: 2018-06-10
forum: General Help
---

### Post by raleigh3 on 2018-06-10
I wrote a script and it outputs this to a file.

Block count:                                   421958912
Reserved block count:        4219589

Is there a way to get it to show the % of reserved blocks?

I know it requires doing some math.

The % reserved blocks equals                     reserved block count divided by block count X 100

---

### Post by spjackson on 2018-06-11
What sort of script? bash, python, perl, something else?

Here's one way... there are many others.

```

#!/bin/bash

block_count=421958912
reserved_block_count=4219589

perl -e "printf(\"%.1lf%%\n\", ($reserved_block_count * 100.0 ) / $block_count);"

```

---

### Post by Claus7 on 2018-06-11
Hello,

as *spjackson* already showed, is better to handle variables with single names: block_count (mind the dash) instead of block count. Now, if your script is in bash the thing is that bash cannot handle non integer values, so bc can be used instead:
> echo "scale=2; $bc/$rbc*100" | bc

where:
'scale 2' gives 2 decimals, adjust it to your liking
'bc' is the block_count variable
'rbc' is the reserved_block_count

Regards!

---

### Post by raleigh3 on 2018-06-11
> **spjackson said:**
> What sort of script? bash, python, perl, something else?

Here's one way... there are many others.

```

#!/bin/bash

block_count=421958912
reserved_block_count=4219589

perl -e "printf(\"%.1lf%%\n\", ($reserved_block_count * 100.0 ) / $block_count);"

```


Thanks.

Not all of the perl line is echoed to the bash script.?

cd /home/andy/Downloads/
echo xxxx | sudo -S tune2fs -l /dev/sda1 > list_tune.txt
# looks for block count and IS case insensitive
#
grep -i "block count" list_tune.txt > list_reserved.txt
echo "#!/bin/bash" > Show_Percent_Reserved_Blocks.sh
echo perl -e "printf(\"%.1lf%%\n\", ($reserved_block_count * 100.0 ) / $block_count);">>Show_Percent_Reserved_Blocks.sh
echo xxxx |sudo -S chmod +x Show_Percent_Reserved_Blocks.sh

---

### Post by raleigh3 on 2018-06-11
This solved the echo problem.
     ```
echo 'perl -e "printf(\"%.1lf%%\n\", ($reserved_block_count * 100.0 ) / $block_count);"' >>Show_Percent_Reserved_Blocks.sh

```
However, when I run Show_Percent_Reserved_Blocks.sh, I get some errors.

```
andyk_~/Downloads$ Show_Percent_Reserved_Blocks.sh
/home/andy/bin/Show_Percent_Reserved_Blocks.sh: line 2: Block: command not found
/home/andy/bin/Show_Percent_Reserved_Blocks.sh: line 3: Reserved: command not found
syntax error at -e line 1, near "/ )"
Execution of -e aborted due to compilation errors.
```

---

### Post by spjackson on 2018-06-12
> **raleigh3 said:**
> 
```

grep -i "block count" list_tune.txt > list_reserved.txt
echo "#!/bin/bash" > Show_Percent_Reserved_Blocks.sh
echo perl -e "printf(\"%.1lf%%\n\", ($reserved_block_count * 100.0 ) / $block_count);">>Show_Percent_Reserved_Blocks.sh

```
You need to set the variables & also you need an extra level of quoting. e.g.
```

block_count=$( grep '^Block count:' list_tune.txt | sed 's/^[^0-9]*//' )
reserved_block_count=$( grep '^Reserved block count:' list_tune.txt | sed 's/^[^0-9]*//' )

echo "#!/bin/bash" > Show_Percent_Reserved_Blocks.sh
echo perl -e "**[COLOR=#ff0000]'[/COLOR]**printf(\"%.1lf%%\n\", ($reserved_block_count * 100.0 ) / $block_count);**[COLOR=#ff0000]'[/COLOR]**">>Show_Percent_Reserved_Blocks.sh

```
I don't understand why you are writing the separate Show_Percent_Reserved_Blocks.sh rather than doing it in the main script, but if you want to do that, the above will work.

---

### Post by raleigh3 on 2018-06-12
I found my problem. As far as I can tell, a perl statement can not be executed from within a bash script.

Any other option?

---

### Post by steeldriver on 2018-06-12
Sure a perl statement may be executed from a shell script

IMHO the cleanest way to pass shell variable values into perl is to use its built-in @ARGV array

You can avoid many of the headaches associated with variable expansion by using a here-document rather than jumping through hoops trying to get the quoting right in a bunch of echo statements e.g.

```

cat > somescript.sh << \EOF
#!/bin/bash

block_count=$(sudo tune2fs -l /dev/sda1 | awk '/^Block count:/ {print $NF}')
reserved_block_count=$(sudo tune2fs -l /dev/sda1 | awk '/^Reserved block count:/ {print $NF}')

perl -e 'printf("%.1lf%%\n", ($ARGV[0] * 100.0 ) / $ARGV[1])' "$reserved_block_count" "$block_count"
EOF

```

---

### Post by raleigh3 on 2018-06-12
Thanks. Worked great.

---

### Post by raleigh3 on 2018-06-12
Is there a way to make somescript.sh executable within somescript.sh so it can be run?

---

