---
title: "how to make a json file 'human readable&quot;"
date: 2023-09-15
forum: General Help
---

### Post by Old Jimma on 2023-09-15
Hello Forum Heros:

I've got a json file that contains the url, logon id, and password for all of the sites I have an account on.

In general, what tool can I uses to read that json file so that it is "human readable:?

Specifically, I'd like to know how to covert that file to a csv file so that I can make more use of it.

Please! No wise cracks! I'm only the piano player!

Thanks,
Old

---

### Post by TheFu on 2023-09-15
This would be a perfect question for an AI.  Some would provide a 15 line script to do it, I'm certain.   Er .... because I just asked for a php code beautifier myself.

BTW, if you find an online tool offering to do this for you, due to the sensitive nature of the data, you shouldn't use it.   Don't post your credentials to an online website. ;)   Unless you have nothing to hide, of course.

---

### Post by dragonfly41 on 2023-09-15
I can suggest what I use (out of many, many options) 

Sublime Text 4

But why convert to csv to make more use of json.
Why not use it as it is.  json.

I am currently writing a list of assets and parsing using configparser.py.

---

### Post by TheFu on 2023-09-15
Some password managers will import CSV, but not json.

---

### Post by Holger_Gehrke on 2023-09-15
To save you some searching, [https://earthly.dev/blog/convert-to-from-json/](https://earthly.dev/blog/convert-to-from-json/) seems like a good explanation and tutorial. Of the three tools he mentions (dasel, jq, jsonv) only jq is in the repositories. They give
```

cat simple.json| jq -r '(map(keys) | add | unique) as $cols | map(. as $row | $cols | map($row[.])) as $rows | $cols, $rows[] | @csv'

```
as one way to do the conversion.

Holger

---

### Post by dragonfly41 on 2023-09-16
> Some password managers will import CSV, but not json.

Since I am following same process of building a password vault I find that BitWarden allows import of .json.

---

### Post by TheFu on 2023-09-16
I've used jq a few times.  I've also written a json parser using Perl (it is a module, so trivial), then used whatever transformation needed to get the data out to a format I needed.  That has been XMLTV and text in a very specific format that could be parsed by another tool for a specific need.  I bet jq could have converted that json to text easier, now that I think about it. ;)

---

### Post by VMC on 2023-09-16
> **Holger_Gehrke said:**
> To save you some searching, [https://earthly.dev/blog/convert-to-from-json/](https://earthly.dev/blog/convert-to-from-json/) seems like a good explanation and tutorial. Of the three tools he mentions (dasel, jq, jsonv) only jq is in the repositories. They give
```

cat simple.json| jq -r '(map(keys) | add | unique) as $cols | map(. as $row | $cols | map($row[.])) as $rows | $cols, $rows[] | @csv'

```
as one way to do the conversion.

Holger

"jq: error (at <stdin>:0): number (146) has no keys"

---

### Post by Holger_Gehrke on 2023-09-16
> **VMC said:**
> "jq: error (at <stdin>:0): number (146) has no keys"

csv is basically a simple table. JSON can hold much more complex structures or even multiple data structures in one file that don't have anything to do with one another structurally. Unless the JSON file is basically an array of structurally identical dictionaries, the given jq command will fail with various errors.

Holger

---

