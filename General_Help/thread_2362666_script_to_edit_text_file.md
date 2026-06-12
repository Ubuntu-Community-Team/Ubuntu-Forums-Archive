---
title: "script to edit text file"
date: 2017-05-31
forum: General Help
---

### Post by orcf on 2017-05-31
hello all

first of all i am new in the community so thanks for all the help you can give me.

i have a file with more then 1000 lines. i want to find some strings and add some text on certain places.

i learning to use sed and awk

a example :

1234567
john
b:
4567891
alice
b:

and so on

i want to find 
1234567
john
b: your address ---- text to add

4567891
alice
b: your address--- text to add

any suggestion?

thanks

---

### Post by TheFu on 2017-05-31
If you want to add the same text after '^b:$', then that is trivial. If you want to do something else, please be clearer in your requirements.

---

### Post by orcf on 2017-05-31
thanks for the reply

the text is always diferente

i have a txt file with the change the address of each name. thats why i want to search the 2 lines first and then add the address

---

### Post by steeldriver on 2017-05-31
Please give us a **minimal working** example - in particular the **format **of the text file containing the addresses and how they are to be matched

---

### Post by TheFu on 2017-06-01
> **orcf said:**
> thanks for the reply

the text is always diferente

i have a txt file with the change the address of each name. thats why i want to search the 2 lines first and then add the address

If I needed to do this 1 time, I'd convert everything into tab-delimited records and sort on the name. If the exact number of both types of records 100%, it would be trivial to use a spreadsheet to merge them. 

The real issue is if any keys (names?) don't match exactly.  Extra spaces are an issue to make a more complex regex match.

---

### Post by Keith_Helms on 2017-06-02
Awk and I think sed both have multiline editing capabilities, but what you want to do is to search for a variable value (id nbr?) and then plug text in a couple of lines down based on matching that value.  Maybe that can be done in awk or sed, but I don't know how.

You CAN do this kind of thing with a bash script.  I set up a couple of files for test data.

1. A master file I called testdata.txt
```

1234567
john
b:
4567891
alice
b:
8675309
jenny
b:
9876543
mary jane
b:

```
2. An update file I called addresses.txt
```

9876543 Mary Jane's Address
4567891 Alice's Address
1234567 John's Address

```

I put together a bash script that reads addresses.txt into an associative array and then processes testdata.txt looking for matches on the id nbr and then plugs in the address if the address for that id nbr is not already present:
```

#!/bin/bash

declare -A addresses
while IFS= read -r line; do
    address=${line#* }
    idnbr=${line%% *}
    addresses[$idnbr]="$address"
done < <( cat addresses.txt )

rm -f newdata.txt
address=""
while IFS= read -r line; do
    if [[ "$line" != "" ]] && [[ "${addresses[$line]}" != "" ]]
    then
        # found a line that matches an id nbr
        address="${addresses[$line]}"
    else
        if [[ "$address" != "" ]]
        then
            if [[ "${#line}" -ge 2 ]] && [[ "${line:0:2}" == "b:" ]]
            then
                if [[ "${#line}" -eq 2 ]]
                then
                    # found a blank line with "b:"
                    line="$line $address"
                fi
                # clear address var so not used for next id nbr
                address=""
            fi
        fi
    fi
    echo "$line" >> newdata.txt
done < <( cat testdata.txt )
# if you're sure this is working, then you can uncomment the next line
# mv newdata.txt testdata.txt
exit

```
If you want to always plug in an address value because you might have an updated one, you could change the following lines
```

                if [[ "${#line}" -eq 2 ]]
                then
                    # found a blank line with "b:"
                    line="$line $address"
                fi

```
To
```

                line="b: $address"

```

After running the script, the output file - newdata.txt - contains the following:
```

1234567
john
b: John's Address
4567891
alice
b: Alice's Address
8675309
jenny
b:
9876543
mary jane
b: Mary Jane's Address

```

See if this script doesn't do what you wanted or at least gives you something to start with.  The script assumes that the id nbr line and the "b:" line do not contain any spaces following the data.  If they do, the script could be modified to handle those.

---

### Post by TheFu on 2017-06-02
Keith, hope you didn't do the homework for the OP. This is a typical homework problem.

---

