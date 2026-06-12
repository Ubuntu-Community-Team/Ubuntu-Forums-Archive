---
title: "Help with a script.... anyone?"
date: 2008-04-09
forum: General Help
---

### Post by msjones on 2008-04-09
Hi.

I am writing a simple automation script to load unload ipwraw/ipw3945 drivers to use with aircrack etc.

Here is my script:

```
if [ $(whoami) = "root" ]
	then clear
	echo "
		Please select one of the following:

		1. Load ipwraw
		2. Load ipw3945

		Make choice"
	read CHOICE
	case $CHOICE in
		1) echo "Loading ipwraw drivers"
			modprobe -r ipw3945
			modprobe ipraw
		2) echo "Loading ipw3945 drivers"
			modprobe -r ipwraw
			modprobe ipw3945
		break ;;
		echo "Please make a choice"
		sleep 3
		continue;;
	esac
		else
		echo "Please run as root"
fi
```

As you can see I want to select either 1 or 2 depending on if I want to load or unload the drivers.

When I execute the scripts I get the following error displayed.

[B]./scan: line 18: syntax error near unexpected token `)'
./scan: line 18: `              2) echo "Loading ipw3945 drivers"'
[/B]

I am new to scripting in general and would appreciate any help I can get!

Thanks in advance!

---

### Post by bodhi.zazen on 2008-04-09
You have to end your cases with ;;

case $variable
1)
commands
;;
2)
commands
;;
*) 
esac

The lase case, *), is a catch all if the $variable does not match any case.

---

### Post by msjones on 2008-04-09
Hi.

I am writing a simple automation script to load unload ipwraw/ipw3945 drivers to use with aircrack etc.

Here is my script:

```
if [ $(whoami) = "root" ]
	then clear
	echo "
		Please select one of the following:

		1. Load ipwraw
		2. Load ipw3945

		Make choice"
	read CHOICE
	case $CHOICE in
		1) echo "Loading ipwraw drivers"
			modprobe -r ipw3945
			modprobe ipraw
		2) echo "Loading ipw3945 drivers"
			modprobe -r ipwraw
			modprobe ipw3945
		break ;;
		echo "Please make a choice"
		sleep 3
		continue;;
	esac
		else
		echo "Please run as root"
fi
```

As you can see I want to select either 1 or 2 depending on if I want to load or unload the drivers.

When I execute the scripts I get the following error displayed.

[B]./scan: line 18: syntax error near unexpected token `)'
./scan: line 18: `              2) echo "Loading ipw3945 drivers"'
[/B]

I am new to scripting in general and would appreciate any help I can get!

Thanks in advance!

---

### Post by bodhi.zazen on 2008-04-09
Please do not start multiple threads on the same question. Please see the answer I already gave you and ask questions if you are having problems.

---

### Post by msjones on 2008-04-09
> **bodhi.zazen said:**
> Please do not start multiple threads on the same question. Please see the answer I already gave you and ask questions if you are having problems.

Hi.

Sorry I didnt post it twice intentionally..... The forums are running very slow and I refreshed my web browser!

apologies!

---

### Post by msjones on 2008-04-09
Right my new script is:

```
if [ $(whoami) = "root" ]
	then clear
	echo "
		Please select one of the following:

		1. Load ipwraw
		2. Load ipw3945

		Make choice"
	read CHOICE
	case $CHOICE in
		1) echo "Loading ipwraw drivers"
			modprobe -r ipw3945
			modprobe ipwraw
			;;
		2) echo "Loading ipw3945 drivers"
			modprobe -r ipwraw
			modprobe ipw3945
			;;
		*)
		echo "Please make a choice"
	esac
		else
		echo "Please run as root"
fi
```

I added in the extras like you advised and all is working great!

Thanks fo your help, very much appriciated!

---

### Post by bodhi.zazen on 2008-04-09
> **msjones said:**
> Hi.

Sorry I didnt post it twice intentionally..... The forums are running very slow and I refreshed my web browser!

apologies!

OK, no problem then, I merged them. Your script should run with minimal modifications, just a matter of the syntax of case.

---

