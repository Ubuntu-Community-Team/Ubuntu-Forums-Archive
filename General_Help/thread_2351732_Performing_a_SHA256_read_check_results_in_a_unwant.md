---
title: "Performing a SHA256 read check results in a unwanted loop?"
date: 2017-02-06
forum: General Help
---

### Post by smartmagnet on 2017-02-06
I have a bunch of files that I would like to generate SHA256 checksums but I'm getting a unwanted loop doing a read check.

For example:

Create two files:
```
mkdir TEST; cd TEST; echo one > one.txt; echo two > two.txt
```

Generate SHA256 checksum file:
```
find . -type f -print0 | sort -z | xargs -0 -n1 sha256sum |tee ../SHA256SUM.txt
2w8b08da5ce60398e1f19af0e5dccc744df274b826abe585eaba68c525434806  ./one.txt
24dd8ed44a83ff94d557f9fd0412ed5a8cbca69ea04922d88c01184a07300a5a  ./two.txt
```

Check the regular files against the newly created checksum file:
```
find . -type f -print0 | sort -z | xargs -0 -n1 sha256sum -c ../SHA256SUM.txt
./one.txt: OK
./two.txt: OK
sha256sum: ./one.txt: no properly formatted SHA256 checksum lines found
./one.txt: OK
./two.txt: OK
sha256sum: ./two.txt: no properly formatted SHA256 checksum lines found
```

Notice the errors "sha256sum: ./one.txt: no properly formatted SHA256 checksum lines found".  Not sure why this is occurring.

Also tried creating checksum without xargs -n1:
```
find . -type f -print0 | sort -z | xargs -0 sha256sum |tee ../SHA256SUM-B.txt
2c8b08da5ce40398e1f19af0e5dccc744df274b826abe585eaba68c525434806  ./one.txt
27dd8ed44a82ff94d557f9fd0412ed5a8cbca69ea04922d88c01184a07300a5a  ./two.txt
```

Check the regular files against the newly created checksum file:
```
find . -type f -print0 | sort -z | xargs -0 sha256sum -c ../SHA256SUM-B.txt
./one.txt: OK
./two.txt: OK
sha256sum: ./one.txt: no properly formatted SHA256 checksum lines found
sha256sum: ./two.txt: no properly formatted SHA256 checksum lines found
```

Again notice the errors "sha256sum: ./one.txt: no properly formatted SHA256 checksum lines found".

Does anyone know why their is a loop check?  The results should be:

```
./one.txt: OK
./two.txt: OK
```

But instead it does a double check with the error "no properly formatted SHA256 checksum lines found".

---

### Post by &amp;KyT$0P# on 2017-02-06
> **smartmagnet said:**
> Check the regular files against the newly created checksum file:
```
find . -type f -print0 | sort -z | xargs -0 -n1 sha256sum -c ../SHA256SUM.txt
./one.txt: OK
./two.txt: OK
sha256sum: ./one.txt: no properly formatted SHA256 checksum lines found
./one.txt: OK
./two.txt: OK
sha256sum: ./two.txt: no properly formatted SHA256 checksum lines found
```

Notice the errors "sha256sum: ./one.txt: no properly formatted SHA256 checksum lines found".  Not sure why this is occurring.
[FONT=Courier New]sha256sum[/FONT] is taking "one.txt" as a list of files and their SHA256 checksums, instead of a file to get the checksum of.  And it is trying to check every file in the lists.

Try replacing that last [FONT=Courier New]find[/FONT] command with just this -
```
sha256sum -c ../SHA256SUM.txt
```

---

