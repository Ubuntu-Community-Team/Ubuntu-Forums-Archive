---
title: "Understanding EVP functions in openssl"
date: 2018-05-07
forum: General Help
---

### Post by jadenbehr123 on 2018-05-07
Hello

I'm trying to complete a task in openssl, it requires the use of EVP API of openssl. I'd appreciate your help with its code.

The goal is to find the right encryption key that's been used to encrypt the following message: "This is a top secret." (21bytes)
The following rules are applied:
[LIST]
[*]The cipher that's been used is AES-128-CBC
[*]Initialization vector has value of zero.
[*]The key that's been used is a word in English whose length is no more than 16 characters. (words that are below 16 characters are to be padded with space character (0x20))
[*]Cipher text is given - (in hex format): "8D20E5056A8D24D0462CE74E4904C1B513E10D1DF4A2EF2AD4540FAE1CA0AAF9"
[*]A words.txt file is given , contains every single word in English.
[/LIST]

This is what I've done:
```

#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <openssl/evp.h> 

void pad(char *word, int len);
void print_result(char *newbuf, char *word, int len, FILE *outFile, char *ismatch);

void main()
{
   unsigned char match[] = "MATCH";
   unsigned char nomatch[] = "NO-MATCH";
   char word[16]; // buffer for each word in words.txt
   FILE *key, *outFile;
   unsigned char outbuf[EVP_MAX_BLOCK_LENGTH], padbuf[EVP_MAX_BLOCK_LENGTH], newbuf[EVP_MAX_BLOCK_LENGTH];
   unsigned char iv[16] = {0}; // iv value is zero
   int i, j,m, buf_len, pad_len, new_len;


   EVP_CIPHER_CTX ctx; // create new cipher context
   EVP_CIPHER_CTX_init(&ctx); 
   char inText[] = "This is a top secret."; // message to be encrypted
   char cipherText[] = "8D20E5056A8D24D0462CE74E4904C1B513E10D1DF4A2EF2AD4540FAE1CA0AAF9";
   //char cipherText[] = {0x8D,0x20,0xE5,0x05,0x6A,0x8D,0x24,0xD0,0x46,0x2C,0xE7,0x4E,0x49,0x04,0xC1,0xB5,
   //                               0x13,0xE1,0x0D,0x1D,0xF4,0xA2,0xEF,0x2A,0xD4,0x54,0x0F,0xAE,0x1C,0xA0,0xAA,0xF9}; // cipher-text

   key = fopen("words.txt","r"); 
   outFile = fopen("matchingResult.txt", "a+");

   while( fgets(word, 16, key) ) // read from words.txt and store in word
   {
      i = strlen(word);
      word[i-1] = '\0'; // remove end-of-line character
      i = strlen(word);
      if( i < 16 ){     // check for words whose length is less than 16 in words.txt
         pad(word,16); // words less than 16 bytes need be padded with space character (0x20) to form 16 byte word
      }


      EVP_EncryptInit_ex(&ctx, EVP_aes_128_cbc(), NULL, word, iv); // set up ctx for encryption
      EVP_EncryptUpdate(&ctx, outbuf, &buf_len, inText, strlen(inText)); // encrypt message and store in outbuf
      EVP_EncryptFinal_ex(&ctx, padbuf, &pad_len); // encrypt data remaining in partial block by padding and store in padbuf

       for(i = 0 ; i < 16; i++){    // copy bytes from both buffers to new buf
        newbuf[i] = outbuf[i];
    }
    for(j = 0 ; j < 16 ; j++, i++){
        newbuf[i] = padbuf[j];
    }    
    newbuf[i] = '\0'; 


    // stuck here
      if( strcmp(cipherText, newbuf) == 0 ) // compare cipher text and buffer content
          print_result(newbuf, word, 32, outFile, match);
      else
          print_result(newbuf, word, 32, outFile, nomatch);
    }
    
    fclose(key);
    fclose(outFile);


}

// print as : word - ciphertext - match
void print_result(char *newbuf, char *word, int len, FILE* outFile, char* ismatch)
{
   int i;
   char crlf = '\n', space = ' ';


   for ( i = 0 ; i < strlen(word) ; i++ ) 
       fprintf(outFile, "%c", word[i]);
   fprintf(outFile, "%c", space);


   for ( i = 0 ; i < len ; i++ )
       fprintf(outFile, "%c", newbuf[i]);
   fprintf(outFile, "%c", space);
   
   for ( i = 0 ; i < strlen(ismatch) ; i++ )
       fprintf(outFile, "%c", ismatch[i]);
   fprintf(outFile, "%c", crlf);
}


void pad(char *word, int len)
{
  int i = strlen(word) ;
  char space = ' ';


  while( i < len )
  { 
     word[i] = space;
     i++ ;
  }
  word[i] = '\0';
}


```

I'd appreciate your help!

---

