---
title: "TPM no longer unlocks device"
date: 2023-10-17
forum: General Help
---

### Post by ichbinjasokreativ on 2023-10-17
My installation of 23.10 worked really nicely until I did a firmware update, after which I always need to enter the recovery key.
Is there a way to fix that?

---

### Post by MAFoElffen on 2023-10-17
Was this an update from fwupdate??? If so, there's a problem which I would considers a being a Bug. If it cleared the TPM, then it cleared the stored passcode for the ecrypted LUKS container... Which is a new, exciting install option that they just started pushing... I don't think they foresaw this kind of thing happening.

Did you backup your installation lately? Ever?

What I would do right now, is, 
Before anything else, get a good backup.
Do ```
cryptsetup luksAddKey /dev/<diskname>
```to add another key to the key slots to be able to get in.
File a bug again fwupdate... This is an unforseen problem that they need to work out so that it doesn't start affecting more people.

If this wasn't from fwupdate, then tell me how the TPM got cleared...

---

### Post by ichbinjasokreativ on 2023-10-18
Thank you for the reply

I installed an update via the new firmware updater tool and then clicked on 'update checksums' (I know it says that it might break the tpm).
I can't add a new passphrase to the device because I only have the recovery key, not the actual passphrase. 'sudo cryptsetup luksAddKey /dev/nvme0n1p4' asks me to enter the current passphrase, which I can't because I don't have it.
If nothing works then I'll just reinstall, I still have all data in a backup, so this would not be a big deal.

There needs to be a way for the user to get the actual passphrase that is used for encryption.

The actual passphrase for the encrypted partition gets generated during the setup process, it then said that I can get the recovery key by typing 'sudo snap recovery --show-keys', but again, the recovery key can only be used to unlock the drive during boot,
not to change/add the actual passphrase.

---

### Post by MAFoElffen on 2023-10-18
I didn't find this in the LUKS docs... But did find mention of it in a discussion of the Debian cryptsetup discussions. When the installer asks if you want a ackup recovery key, it then generates a passphrase to use as a recoverykey, and stores it in LUKS key - slot 2... So when you add another passphrase, keyfile or use TPM2 systemd-cryptenroll, you can use that recoverykey-passphrase to update it or add more keys...

RE: [https://0pointer.net/blog/unlocking-luks2-volumes-with-tpm2-fido2-pkcs11-security-hardware-on-systemd-248.html](https://0pointer.net/blog/unlocking-luks2-volumes-with-tpm2-fido2-pkcs11-security-hardware-on-systemd-248.html)
> 
 There's still plenty room for further improvement in all of this. In particular for the TPM2 case: what the text above doesn't really mention is that binding your encrypted volume unlocking to specific software versions (i.e. kernel + initrd + OS versions) actually sucks hard: if you naively update your system to newer versions you might lose access to your TPM2 enrolled keys (which isn't terrible, after all you did enroll a recovery key &#8212; *right*? &#8212; which you then can use to regain access). To solve this some more integration with distributions would be necessary: whenever they upgrade the system they'd have to make sure to enroll the TPM2 again &#8212; with the PCR hashes matching the new version. And whenever they remove an old version of the system they need to remove the old TPM2 enrollment. 

I just started reading this, which may help you. Not positive yet if something from there can be used to re-key the TPM yet, but looks promising.
RE: [https://blastrock.github.io/fde-tpm-sb.html](https://blastrock.github.io/fde-tpm-sb.html)

It has instructions on how to write it to the tpm initially... In a new install.

But... I still feel that this was a known risk, and should be brought up to launchpad. As it said... It is experimental. I think this is going to happen to other people also, not just you. And not sure yet, if there is yet some kind of dkms process tha reseals the TPM for a Kernel Update. As mentioned in the quotes about. I'm pretty sure that is in place... But if in place, there might be a mechanism there, to re-enroll your tpm. 

Thinking.

---

### Post by MAFoElffen on 2023-10-18
I'm thinking, it you add one more key to the Luks key - slots, that will gve you a fail-back way in, in case something goes wrong... then delete the first key - slot. That should be the TPM key. Gen a key key for that add that key to the first slot, then save that to the TPM.

The TPM should not be a worry in overwriting a slot, because it was cleared.

---

### Post by MAFoElffen on 2023-10-18
Okay. I installed 23.10 as encrypted TPM in a VM and zero'ed the TPM so I could replicate the problem and tested this. It works, and should solve your problem.
```

sudo su
grep . /etc/cryptab
# Save the information from the tpm unlock line
ls -l /dev/disk/by-id
# Use ls -l /dev/disk/by-id to get the information of this to change "<luks_root_partition>" to that information...
# That partition will include "-part#'" to identify which partition on that disk it is...
LuksPartition=/dev/disk/by-id/<luks_root_partition>
# Verify that is the correct partition
blkid $LuksPartition
# Verify that the output says TYPE="crypto_LUKS"

cryptsetup -v open --test-passphrase $LuksPartition
# This will tell you the key - slot of the recovery key key-slot

# add a new key as a backup passphrase
crypsetup -v lukAddKeys $LuksPartition
# Enter the recovery key to confirm it
# Will tell you which key-slot it adds it to

cryptsetup luksDump $LuksPartition | grep 'Key Slot [0-7]:'
# fFind the other key slot (1 of 3) that wasn't indicated above
# Most likely Key Slot 0(?)

# Adjust the number at the end of this to that key-slot
crysetup -v luksKillSlot $LuksPartition 0
dd if=/dev/random bs=64 count=1 | xxd -p -c999 | tr -d '\n' > /root/luks_key
cryptsetup luksAddKey $LuksPartition /root/luks_key --pbkdf-force-iterations=4 --pbkdf-parallel=1  --pbkdf-memory=32
## Enter any existing passphrase: <enter your existing recovery key or new passphrase here>

# Seal the TPM with the new key...
tpm2-initramfs-tool seal --data $(cat /root/luks_key) --pcrs 0,2,7

```
EDIT: To write this post, I had to use "key-slot" instead of that, without the dash... The Forum filter if done without the dash, filters into ke***** .

I would back up that TPM key somewhere in a USB Flash Drive, kept some secure, as a backup, in case this happens again, before deleting it from the root's user directory... That way, if it happens again, all you will have to do it, is rewrite that backed key to your TPM.

---

### Post by ichbinjasokreativ on 2023-10-18
Thank you for taking the time to write this answer, but I cannot follow along because the recovery key apparently doesn't count as one of the passphrases for the encrypted drive. Unlocking at boot works with the recovery key, but for example ' [COLOR=#E8E6E3][FONT=&amp]cryptsetup -v luksAddKey $LuksPartition[/FONT][/COLOR]' asks for 'any available passphrase', but does not accept the recovery key.
I'm going to reinstall.

---

### Post by MAFoElffen on 2023-10-18
Dang. The doc's say the recovery key is considered as a passphrase. It worked on the VM I created, but then again, I setup the recovery key during the install and backed it up to a USB drive, just after the install completed, before rebooting for the first reboot...

That doesn't work on yours as a passphrase? [s]It works on this VM(???)[/s] Oh well.

[s]Wait... --showkeys should not work for you with LUKS2. Did that show you a key?[/s] Nevermind, I respun it and saw it again...
```

sudo snap recover --show-keys

```
Yes. If the key doesn't count as a passphrase on yours, then you have no choice but to re-install Because you cannot add or change a key without a valid passphrase or a key file....

EDIT: You are right, It lets me open the volumes... with the recovery key... Only on boot... But that is not what is being used to unlock the LUKS containers directly, both /dev/sda3 and /dev/sda4 (both are LUKS...)

---

### Post by MAFoElffen on 2023-10-18
I started this Bug Report, as i could recreate what was going on: [https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2039741](https://bugs.launchpad.net/ubuntu-desktop-installer/+bug/2039741)

You might want to select the link as "Also affected"... So they know it is not just an isolated, one-time, only affects one-user kind of thing.

---

### Post by ichbinjasokreativ on 2023-10-19
Thank you for taking the time to look into this. Bugs are bad, but I'm kinda happy that you can confirm my issue.
Kind of crazy that we found this, verifying that the recovery key is actually useful for unlocking the disk should've been tested more thoroughly.
Thank you for creating the bug report.

I reinstalled without tpm encryption, I'll have to look into involving the tpm in a post-installation scenario.

---

### Post by coffeecat on 2023-10-19
> **MAFoElffen said:**
> 
EDIT: To write this post, I had to use "key-slot" instead of that, without the dash... The Forum filter if done without the dash, filters into ke***** .

A bit OT, but for the record: I have no idea why a past forum admin, at about the time dinosaurs roamed the planet, decided that the string "yslot" was too coarse for delicate forum members' ears, but since Google doesn't come up with anything remotely relevant, and I'm not aware of any obscene context for it, I've removed yslot from the forum censor list. :)

---

### Post by #&amp;thj^% on 2023-10-19
^^^^:lolflag:

---

### Post by MAFoElffen on 2023-10-20
^^^ Hooray!!! Thank you coffeecat! I had no idea why that was hitting the censor/filter. Now I have at least an idea why. LOL!

---

### Post by ichbinjasokreativ on 2023-10-20
In case anybody finds this in the future:
Thank you  to [https://lemmy.world/u/skullgiver@popplesburger.hilciferous.nl](https://lemmy.world/u/skullgiver@popplesburger.hilciferous.nl) for providing a way to recover the real key out of the encoded recovery key:

You can add up to 32 key slots for a LUKS2 volume, and every one of those will allow you to add or remove keys. I have done so myself using a key file at one point. If you have any working key, you can add a new key to your system. Your recovery key would’ve worked if it was generated by systemd-enroll rather than whatever Ubuntu did.

To fix the problem you have, “recovery keys” need to be turned into real keys. After a bit of conversion, Snap will just call cryptsetup like a normal Linux install would: [*cmdAddRecoveryKey.Execute()]("https://github.com/snapcore/snapd/blob/420a9a2169fbf62505cbf5aba8d088993b242ba7/cmd/snap-fde-keymgr/main.go#L108") -> [AddRecoveryKeyToLUKSDevice]("https://github.com/snapcore/snapd/blob/420a9a2169fbf62505cbf5aba8d088993b242ba7/secboot/keymgr/keymgr_luks2.go#L105") -> [AddRecoveryKeyToLUKSDeviceUsingKey]("https://github.com/snapcore/snapd/blob/420a9a2169fbf62505cbf5aba8d088993b242ba7/secboot/keymgr/keymgr_luks2.go#L120C29-L120C29") -> [AddKey]("https://github.com/snapcore/snapd/blob/420a9a2169fbf62505cbf5aba8d088993b242ba7/secboot/luks2/cryptsetup.go#L119").

All the “recovery key” mechanism is doing is generate a key by itself (a very secure key, but just a normal key nonetheless) and pass it on through to [cryptsetup]("https://github.com/snapcore/snapd/blob/420a9a2169fbf62505cbf5aba8d088993b242ba7/secboot/luks2/cryptsetup.go#L157C13-L157C13"). This key isn’t a normal string you can type in (as it’s purely random), which is why it’s encoded in a weird integer format that’s easy to type into a numpad.

The snap commands aren’t printing the real key, they’re converting your input to keys during boot. However, if the drive unlocks at all, the user can add a new key, if they can just find how to get the real key out of their system. [runFDERevealKeyCommand]("https://github.com/snapcore/snapd/blob/420a9a2169fbf62505cbf5aba8d088993b242ba7/kernel/fde/reveal_key.go#L50C23-L50C23") seems very suspect to me, I believe that command will dump the real key out, though I can’t find the source. I think you need to run fde-reveal-key and feed it something (JSON, I think?).

[This post]("https://forum.snapcraft.io/t/uc20-fde-boot-flow/27895/13") contains a Go program that will decode the actual key from whatever Snap/Ubuntu turned it into and mount the partition; the parsing code was taken [from Snap itself]("https://github.com/snapcore/secboot/blob/master/crypt.go"). I’ve taken the code and thrown together the following program to decode the key for your:
package main

```

import (
	"encoding/binary"
	"errors"
	"fmt"
	"os"
	"strconv"
)

// ParseRecoveryKey Parse[16]byte interprets the supplied string and returns the corresponding [16]byte. The recovery key is a
// 16-byte number, and the formatted version of this is represented as 8 5-digit zero-extended base-10 numbers (each
// with a range of 00000-65535) which may be separated by an optional '-', eg:
//
// "61665-00531-54469-09783-47273-19035-40077-28287"
//
// The formatted version of the recovery key is designed to be able to be inputted on a numeric keypad.
func ParseRecoveryKey(s string) (out [16]byte, err error) {
	for i := 0; i &lt; 8; i++ {
		if len(s) &lt; 5 {
			return [16]byte{}, errors.New("incorrectly formatted: insufficient characters")
		}
		x, err := strconv.ParseUint(s[0:5], 10, 16) // Base 10 16 bit int
		if err != nil {
			return [16]byte{}, errors.New("incorrectly formatted")
		}
		binary.LittleEndian.PutUint16(out[i*2:], uint16(x))

		// Move to the next 5 digits
		s = s[5:]
		// Permit each set of 5 digits to be separated by an optional '-', but don't allow the formatted key to end or begin with one.
		if len(s) > 1 &amp;&amp; s[0] == '-' {
			s = s[1:]
		}
	}

	if len(s) > 0 {
		return [16]byte{}, errors.New("incorrectly formatted: too many characters")
	}

	return
}

func selfTest() bool {
	_, e := ParseRecoveryKey("61665-00531-54469-09783-47273-19035-40077-28287")

	if e != nil {
		return false
	} else {
		return true
	}
}

func main() {
	if !selfTest() {
		fmt.Println("Self-test failed, something went wrong during compilation")
		return
	}

	fmt.Println("Please enter your Snap-encoded recovery key below:")
	var recoveryKey string
	_, err := fmt.Scanln(&amp;recoveryKey)
	if err != nil {
		fmt.Println("Failed to read your key!")
	}

	if key, e := ParseRecoveryKey(recoveryKey); e != nil {
		fmt.Printf("Failed to decode recovery key; %s\n", e)
	} else {
		fmt.Printf("Your recovery key is: ")
		_, _ = os.Stderr.Write(key[:])
		fmt.Println()
	}
}

```
Steps to run that program:

[LIST=1]
[*][Install Go]("https://go.dev/doc/install")
[*]Save the file somewhere (recover.go)
[*]Run the command go run recover.go
[/LIST]
You will find the key dumped into the terminal, but there’s a good chance this is Unicode gibberish. Run the following command to save the key to a file: go run recover.go 2> key.txt; that will dump the key to key.txt rather than print it out. You can then use key.txt to add another key to a LUKS container, for example: cryptsetup luksAddKey --key-file=key.txt /dev/sda4 newkeyheremakesureitsverysecure.

What I don’t get, is why the Ubuntu folks didn’t take the 16-byte key they generated, turned it into their own weird key format, and use that as a key string. That would keep their generation compatible with cryptsetup, would make the key equally easy to enter and equally secure, and wouldn’t expose these weird bugs. It would’ve cost what, 32 extra bytes in memory?

---

### Post by MAFoElffen on 2023-10-20
Thank you for finding and posting that! (But... In the nicest way)

Please... Go back to your post > Select "Edit" > Select "Go Advanced" to get into the Advanced Editor with the extended toolbar > Seelct the text of the code with your mouse. > Select the "#" icon to wrap the code with inserted CODE Tags > Save/Submit.

A forum policy to only post code and raw output within CODE Tags...

[hr][/hr]
I'm going to try that and see what it comes up with...

---

### Post by MAFoElffen on 2023-10-20
I get sysntax errors with that posted code:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ go run ./recovery.go
# command-line-arguments
./recovery.go:19:22: syntax error: unexpected semicolon, expected { after for clause
./recovery.go:32:26: syntax error: unexpected semicolon, expected { after if clause
./recovery.go:62:27: syntax error: unexpected semicolon in argument list; possibly missing comma or )

```
Going to look at it...

EDIT: I debugged it, and it is useless to be able to use a key. What was wrong, syntax wise, is that what got displayed in the code in that post, mistakenly mixed in HTML codes for characters. I got it debugged and it ran without errors, BUT: What got decoded for my test cases translated recovery code was jibberish. The console cannot display raw hex characters. And his redirection example doesn't work. It then errors as "file not found", because it doesn't give the user a chance to enter the recovery code.

I know a lot of programming languages, but golang is not one of them. What would need to be able to use that code, is to modify it to write the keyfile directly to a file, instead of trying to display it on the console.

Dang. I was hopeful.

EDIT2: I created an account there to ask him if he can add that to his code... Waiting on my account there being approved by the admin's

---

### Post by MAFoElffen on 2023-10-20
I posted there asking...

---

### Post by MAFoElffen on 2023-10-21
We worked it out into a working GoLang script that generates a valid hex key-file translated from the recovery key...

I tested it on the VM and it unlocks both LUKS Containers and I was able to add new passphrases to the key-slots. 

Late right now. Will get back to this tomorrow.

---

