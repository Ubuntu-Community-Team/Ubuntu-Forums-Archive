---
title: "How to add data at a specific place to a file"
date: 2015-11-08
forum: General Help
---

### Post by polaris90 on 2015-11-08
for example if I have the following data in a fie
<!DOCTYPE html>
<html>
<body>


	<h1>What Can JavaScript Do?</h1>
	<p id="demo">JavaScript can change HTML content.</p>
	
</body>
</html>

and I want to add "<food>" between the header and the body

<!DOCTYPE html>
<html>
<body>


	<h1>What Can JavaScript Do?</h1>
        <food>
	<p id="demo">JavaScript can change HTML content.</p>
	
</body>
</html>



How can I issue a command to do this. I found online that I can use awk or sed but all the examples I found are for printing data and not adding it to a file. Can anybody help me with this one?

---

### Post by sotiris2 on 2015-11-08
Is the sed/awk output the whole file? In linux command line you can redirect anything output to the screen to a file like this. [code]command > file [\code]

Where command put the sed command & arguments and in file put f.e. edit.html but please not the same filename as the file you are trying to alter. If the edited file is correct you can then delete the original and rename it.

---

### Post by matt_symes on 2015-11-08
Hi

You can insert a line after a line that contains a pattern match.

You need the -i (in-place) modifier for sed.

```
<!DOCTYPE html>
<html>
<body>
<h1>What Can JavaScript Do?</h1>
<p id="demo">JavaScript can change HTML content.</p>
</body>
</html>

```

```
sed -i '/<body>/a <food>' test.txt
```
```

matthew-laptop:/home/matthew:2 % sed -i '/<body>/a <food>' test.txt
matthew-laptop:/home/matthew:2 % cat test.txt 
<!DOCTYPE html>
<html>
<body>
<food>
<h1>What Can JavaScript Do?</h1>
<p id="demo">JavaScript can change HTML content.</p>
</body>
</html>
matthew-laptop:/home/matthew:2 % 
```

You really need to read a good book or some online tutorials for sed though as the topic is large.

Make sure the book and the tutorials are for GNU sed.

Kind regards

---

