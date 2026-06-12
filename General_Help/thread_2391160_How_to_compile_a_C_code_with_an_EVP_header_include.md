---
title: "How to compile a C code with an EVP header included"
date: 2018-05-06
forum: General Help
---

### Post by jadenbehr123 on 2018-05-06
Hello

I'm trying to create a small program in C which uses the EVP API of Openssl to encrypt/decrypt a message on my Ubuntu(12.04) VM.

My problem is I'm unable to compile my file, because of the EVP header that is included in the code.

The include files are located in - Home > openssl-1.0.1 > include > openssl

and I created a file.c on the desktop.


I would appreciate your help
Thank you

---

### Post by steeldriver on 2018-05-06
Hello and welcome to the forums

Since the header file is not in a "standard" location, the compiler will need to be told where to find it using a `-I` include directive e.g.

```

cd ~/Desktop
gcc -o yourprog -I ~/openssl-1.0.1/include/openssl/ file.c

```

You may need to do a similar thing for non-standard library paths using `-L`

---

### Post by jadenbehr123 on 2018-05-06
> **steeldriver said:**
> Hello and welcome to the forums

Since the header file is not in a "standard" location, the compiler will need to be told where to find it using a `-I` include directive e.g.

```

cd ~/Desktop
gcc -o yourprog -I ~/openssl-1.0.1/include/openssl/ file.c

```

You may need to do a similar thing for non-standard library paths using `-L`

Thank you for your answer. However, I am still getting an undefined reference to all EVP functions.

Let me attach a screenshot:
[[IMG]https://preview.ibb.co/cf3uw7/Capture.jpg[/IMG]]("https://ibb.co/n53uw7")

---

### Post by steeldriver on 2018-05-06
You will also need to link the appropriate library / libraries and likely specify the path like I mentioned e.g.

```

-L ~/openssl-1.0.1/lib  -lssl -lcrypto

```

(adjust the -L path appropriately for the actual location of libssl and libcrypto)

---

