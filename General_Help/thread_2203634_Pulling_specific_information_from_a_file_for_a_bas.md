---
title: "Pulling specific information from a file for a bash script"
date: 2014-02-04
forum: General Help
---

### Post by hoopia on 2014-02-04
This is a bit challenging for me, as it requires pulling out specific information for a bash script that I am writing.

I would like to set a variable to a folder location found in a configuration file, and I would ultimately like to delete certain file types within that folder. For example:

location="/home/Downloads"
rm $location/*.txt

This would remove all txt files found within $location. However, I don't want to define location this way, I want to define it based on text found in another file. If there is a file called **config.conf** and it contains this line:

 "location_of_text_files": "/home/Downloads",

I want to be able to search on "location_of_text_files" and then pull out the directory as a string to be used in defining my variable. I imagine this would require a combination of grep and sed, but I don't know how to do this.

---

### Post by erind on 2014-02-04
> **rushi4687 said:**
> [...]

location="/home/Downloads"
rm $location/*.txt

This would remove all txt files found within $location. However, I don't want to define location this way, I want to define it based on text found in another file. If there is a file called **config.conf** and it contains this line:

 **"location_of_text_files": "/home/Downloads",**

I want to be able to search on "location_of_text_files" and then pull out the directory as a string to be used in defining my variable. I imagine this would require a combination of grep and sed, but I don't know how to do this.

It's not that hard, but it depends on the exact format of your *config.conf* file, especially the* "location_of_text_files"* line. Assuming the format shown above and if the *"location_of_text_files"* is found only *once* in the file, one way using grep would be:

```
location="$(grep -Po '(?<="location_of_text_files":\s").*(?=",)' config.conf)"

```
Then always use double quotes when referring it as a variable:

```
ls -l [COLOR=#0000ff]**"**[/COLOR]$location[COLOR=#0000ff]**"**[/COLOR]/*.txt
```

---

### Post by hoopia on 2014-02-04
That works perfectly, thank you!

---

