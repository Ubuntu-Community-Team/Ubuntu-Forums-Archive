---
title: "Questions about making shell script"
date: 2007-07-04
forum: General Help
---

### Post by Ebuntor on 2007-07-04
Hi everyone,
 
 I'm writing a (somewhat complex) shell script and I need a little help. The script's purpose is to print certain forms selected by the user. It will run on a computer at my sport club so it needs to be foolproof.
 
 What the user will need to see is:
 *What forms would you like to print?*
 *Form 1 <press 1>*
 *Form 2 <press 2>*
 *Form 3 <press 3> * 
 
 Followed by a “are you sure?” “yes” “no” dialog.
 
 I've been using linuxcommand.org as guide and [this script]("http://doc.gwos.org/index.php/Firefox_%26_Thunderbird_icon") as an example (since it's similar) but it's proofing to be a lot more complex than I expected. My question is are there any programs that help me to write a script and is there any way to make a GUI for this script instead of a CLI (apart from using a programming language)?

**[SIZE=2] Or is there an existing script or program that can do this?[/SIZE]** I haven't been able to find any in the repositories.


EDIT: One more question: What's the terminal command to print a file?

---

### Post by Bavo on 2007-07-04
> **Ebuntor said:**
> Hi everyone,
 
 I'm writing a (somewhat complex) shell script and I need a little help. The script's purpose is to print certain forms selected by the user. It will run on a computer at my sport club so it needs to be foolproof.
 
 What the user will need to see is:
 *What forms would you like to print?*
 *Form 1 <press 1>*
 *Form 2 <press 2>*
 *Form 3 <press 3> * 
 
 Followed by a “are you sure?” “yes” “no” dialog.
 
 I've been using linuxcommand.org as guide and [this script]("http://doc.gwos.org/index.php/Firefox_%26_Thunderbird_icon") as an example (since it's similar) but it's proofing to be a lot more complex than I expected. My question is are there any programs that help me to write a script and is there any way to make a GUI for this script instead of a CLI (apart from using a programming language)?

**[SIZE=2] Or is there an existing script or program that can do this?[/SIZE]** I haven't been able to find any in the repositories.


EDIT: One more question: What's the terminal command to print a file?

Something like this maybe?

```

number="flef"
while [ $number = "flef" ]; do
echo "What forms would you like to print?"
echo "Form 1 <press 1>"
echo "Form 2 <press 2>"
echo "Form 3 <press 3>"
read number
case "$number" in
        1) lp form1;
        ;;
        2) lp form 2;
        ;;
        *) echo "$number is not a correct choice!";
        number="flef";
        ;;
esac
done

```

---

### Post by Ebuntor on 2007-07-04
> **Bavo said:**
> Something like this maybe?

```

number="flef"
while [ $number = "flef" ]; do
echo "What forms would you like to print?"
echo "Form 1 <press 1>"
echo "Form 2 <press 2>"
echo "Form 3 <press 3>"
read number
case "$number" in
        1) lp form1;
        ;;
        2) lp form 2;
        ;;
        *) echo "$number is not a correct choice!";
        number="flef";
        ;;
esac
done

```

Thank you! That's exactly what I was looking for. :D

---

### Post by reclusivemonkey on 2007-07-04
Assuming you are using Gnome, Zenity will give you some GUI options.

---

