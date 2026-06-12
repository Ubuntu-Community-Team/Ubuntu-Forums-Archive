---
title: "Terminal input serial commands, output Arduino Tx"
date: 2014-04-06
forum: General Help
---

### Post by imbatronics on 2014-04-06
Hi there guys

I am somewhat of a beginner in this space ):P

I am using Arduino Mega2560 and interfacing it with a coin machine from a vending machine.
The coin machine runs on a protocol called MDB (multi-drop bus) which is 9bit serial.
I would normally use the Arduino IDE but that does not cater for 9-bit serial. I have therefore decided to code using c. I have come across a usart setup function which can bitbash into 9bit mode.
I have installed avr-gcc avr-libc avrdude.

The coin machine acts depending on serial data it recieves. i.e to reset it needs to read 100101010 from its Rx (this is a random 9-bit number, I am not sure what the true number is at this moment).
Another example would be if it recieves 10101111 on Rx it would dispense a coin of desired type etc.
There are also various other commands like ack,poll, etc.
So what I want to do is send the appropriate binary numbers out from the Arduino's Tx and into the coin machine's Rx and try get communication with the coin machine.

This was just for context but my main question is more general (lets assume we are working in 8bit mode):

a) how can I type a 8bit binary number (e.g 10111010) on the terminal, and have that number be put on the Tx line of the arduno.
b) since the mega2560 has 3 Tx/Rx modules, can I Tx from one module and Rx from another module, for testing, such that the 8bit binary number I type in terminal appears on the terminal too.

note: The reason I want the numbers to be represented in binary is because I want to see each bit, it will make more sense to me that way

Thank you kindly!

---

