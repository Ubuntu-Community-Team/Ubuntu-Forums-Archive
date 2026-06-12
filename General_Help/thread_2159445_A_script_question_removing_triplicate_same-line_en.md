---
title: "A script question: removing triplicate same-line entries"
date: 2013-07-03
forum: General Help
---

### Post by SuaSwe on 2013-07-03
Hello my fellow Ubuntuers!

I have a scripting conundrum I'm trying to figure out; it involves removing a particular string from a large aliases file, as follows:

```

# original aliases file
various_different: various_different
emailaddresses: emailaddresses, emailaddresses
some-with-numbers0: some-with-numbers0, some-with-numbers0
some_with_special_chars: some_with_special_chars, some_with_special_chars

# desired aliases file
various_different: various_different
emailaddresses: emailaddresses
some-with-numbers0: some-with-numbers0
some_with_special_chars: some_with_special_chars

```

E.g.: I want to get rid of any triplicate entries on the same line but without disrupting the lines themselves. I believe some combination of arrays and awk can do this but am not sure how. :) Note that the triplicate entries may not be always be in a particular field. 

Thanks all!

SuaSwe

---

### Post by SuaSwe on 2013-07-03
Good news, everyone - with the help of a colleague, the mystery has been solved! After much pondering we came up with the following solution:

```

$ cat examplefile | while read x; do
	VAR1=$(echo $x | sed 's_:.*$__')
	VAR2=$(echo $x | sed 's_^.*: __' | sed 's_,__g' | tr ' ' '\n' | sort -u | tr '\n' ',' | sed 's_,$__')
	echo $VAR1: $VAR2
done

```

So to explain: 

- First we saved the first entry on each line as VAR1 by removing everything after the comma ( sed 's_:.*$__' )
- We then made VAR2 by removing everything up to the comma ( sed 's_^.*: __' ), without commas ( sed 's_,__g' ), splitting into "separate lines" though they will still appear on the same line if "VAR2" is echoed ( tr ' ' '\n' ), sorting and uniqing the output ( sort -u ), adding the commas back in place of each "new line" which still appear as being on a single line when the variable is printed ( tr '\n' ','  ), and finally removing the commas from the end of the line ( sed 's_,$__'  )
- We then echoed $VAR1, put a colon and space after, followed by $VAR2

.... and ta-dah! I've got the output I required. Pleased as punch. :)

---

