---
title: "sed question"
date: 2019-12-11
forum: General Help
---

### Post by Patrick_Burger on 2019-12-11
Not sure where this goes. could use some help though.

```

string=kjnsdfbhiawbsfkjPATTERNTOMATCHfwerofnuoHIUJKNJBKPATTERNTOMATCHwetgerdghserytryhserryswPATTERNTOMATCHsdgdheryhrthyseyasrehdtrhyPATTERNTOMATCHJFJKBIjkbiugBKJbKhlb
```

I am trying to strip out everything before  the FIRST "PATTERNTOMATCH" but keep the rest of them. tried:
```
echo $string | sed 's/.*PATTERNTOMATCH/PATTERNTOMATCH/'
```
should return
```
PATTERNTOMATCHfwerofnuoHIUJKNJBKPATTERNTOMATCHwetgerdghserytryhserryswPATTERNTOMATCHsdgdheryhrthyseyasrehdtrhyPATTERNTOMATCHJFJKBIjkbiugBKJbKhlb
```
returns
```
kjnsdfbhiawbsfkjfwerofnuoHIUJKNJBKwetgerdghserytryhserryswsdgdheryhrthyseyasrehdtrhyJFJKBIjkbiugBKJbKhlb
```

need some help with this.\

also tried being more emphatic
```
echo $string | sed 's/.*PATTERNTOMATCH/PATTERNTOMATCH/1'
```
same results

for argument's sake the gibberish is also base64 code too long to simulate here but the gibberish before the first PATTERNTOMATCH is a tag that's appended to it.

---

### Post by Impavidus on 2019-12-11
Without using sed at all, just bash string manipulation:```
# Define the string
string=kjnsdfbhiawbsfkjPATTERNTOMATCHfwerofnuoHIUJKNJBKPATTERNTOMATCHwetgerdghserytryhserryswPATTERNTOMATCHsdgdheryhrthyseyasrehdtrhyPATTERNTOMATCHJFJKBIjkbiugBKJbKhlb

# Find the first occurence of PATTERNTOMATCH
position=$(expr index "$string" PATTERNTOMATCH)

# Subtract one
let "position -= 1"

# Print the substring starting at this position
echo ${string:$position}
```

---

### Post by Holger_Gehrke on 2019-12-11
Can't quite get sed to misbehave as it does for you. Actually I can reproduce the result easily enough (sed 's/PATTERNTOMATCH//g') but if I execute the line you give I get
```

echo $string| sed 's/.*PATTERNTOMATCH/PATTERNTOMATCH/'
PATTERNTOMATCHJFJKBIjkbiugBKJbKhlb

```
and that's actually explainable: The .* at the beginning is greedy, meaning it will take as many characters as possible and will therefore 'eat' all but the last PATTERNTOMATCH. If you were using Perl compatible RE you could use the 'non-greedy' variant of * (I think that's '*?') or you could rewrite as
```

echo $string| sed -E 's/.*PATTERNTOMATCH(.+)PATTERNTOMATCH(.+)PATTERNTOMATCH(.+)PATTERNTOMATCH(.+)/PATTERNTOMATCH\1PATTERNTOMATCH\2PATTERNTOMATCH\3PATTERNTOMATCH\4/'

```
The option '-E' turns on extended regular expressions.

Whether or not this works for you I can't tell because I can't reproduce your error precisely.

And of course Impavidus' 'sed-less' solution is more elegant than this ...

And for another 'sed-less' solution (shorter but a bit more cryptic)
```

echo PATTERNTOMATCH${string#*PATTERNTOMATCH}

```
See  'man bash' section  'Parameter Expansion'. ${var#pattern} removes the  shortest string that matches pattern from the beginning of var (since  PATTERNTOMATCH gets removed, I added it back in the echo-command).

Holger

---

