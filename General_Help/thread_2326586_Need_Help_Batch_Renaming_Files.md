---
title: "Need Help Batch Renaming Files"
date: 2016-06-02
forum: General Help
---

### Post by false_chicken on 2016-06-02
[FONT=Helvetica]I was rapidly changing permissions on a folder that has tons of files and I use Syncthing. Now every file in the folder has conflicted. This is reflected on both of my clients. So I cannot simply restore from the opposite one. No originals exist. I am sorta in a panic as my backup is a few days old and I did a lot of work in that time and since this folder has git repositories in it manually renaming is not feasible. Does anyone know of some bash fu to remove the sync-conflict-(date) on all the files? For example the file "README.sync-conflict-20160602-094947.txt" needs to be renamed to "README.txt". This is true for thousands of files. As far as I can tell the length of the date stamps are always the same. So being able to remove ".sync-conflict-datelength" would be useful. [/FONT][FONT=Helvetica]Thanks so much.[/FONT]

---

### Post by ashwin.kj on 2016-06-02
Hi
I am not good with bash commands, but if you can make do with C++, take a look at the following
```

#include<fstream>
#include<string.h>
#include<iostream>
#include<dirent.h>

using namespace std;

void renameFiles() {
    string str;
    DIR *pDIR;
    struct dirent *entry;
    if ((pDIR = opendir(".")) != NULL) {
        /* Read all the files and folder in current directory */
        while ((entry = readdir(pDIR)) != NULL) {
            /* Skipping the . and .. */
            if (strcmp(entry->d_name, ".") != 0 && strcmp(entry->d_name, "..") !=0) {
                string FileName = entry->d_name;
                string FileNameMod;
                if (FileName.find("sync-conflict-") != string::npos) {
                    auto pos = FileName.find("sync-conflict-");
                    FileNameMod = FileName.substr(0,pos);
                    /* Under the assumption that (date stamp) length is constant */
                    FileNameMod = FileNameMod+ FileName.substr(pos+30,FileName.size());
                    cout << FileName << " renamed to " << FileNameMod << "\n";
                    string sysCall = "mv " + FileName + " " + FileNameMod;
                    /* Uncomment when you sure this is what you want */
                    /* system(sysCall.c_str()); */
                }
            }
        }
        closedir(pDIR);
    } else {
        /* If not able to open the directory */
        perror("");
    }
}

int main() {
    renameFiles();
    return 0;
}

```
Compile the code using
```
g++ -std=c++11 <filenameYouGave> -o Rename.out
```
It essentially goes through your directory from which the complied C++ file is called and then for all the files/folder that have "sync-conflict-" in their name, renames it. I have taken the assumption that the date stamp length is constant.
Also I have commented out the actual rename command "system (sysCall.c_str())". Test run the code and if you think it is working then you can uncomment that line and re-complie and execute.
Hope this helps

---

### Post by steeldriver on 2016-06-02
I'd suggest trying

```

find . -type f -name '*.sync-conflict-*' -execdir rename -vn -- 's/\.sync-conflict-\d+-\d+//' {} +

```

It won't rename anything until you remove the '-n' (no-op) flag: see whether it is doing the right thing, the Ctrl-C if necessary and only re-run for real when you're SURE it's doing what you want

DISCLAIMER: I have no idea what Syncthing is or whether what you want to do makes sense

---

### Post by HermanAB on 2016-06-03
A bash find one liner compared to the above C program is a fine example of why I love *NIX.

---

