---
layout: post
title:  "Github"
date:   2016-09-22
---
How to generate ssh key and adding it to ssh agent?
SSH keys are a way to identify trusted computers without involving passwords. It is a common way to connect securely to remote machines. They are based on the SSH cryptographic network protocol, which is responsible for the encryption of the information stream between you and the remote machine. Ultimately, using SSH keys, you can connect to your VM without even entering a password . It is not possible to crack your password. I must say that it is more secure and you can also increase security even more by protecting the private key with a passphrase. You can generate an SSH key and add the public key to your GitHub account. 

You might be wondering how is this possible? 

Well, SSH is based on public-key cryptography. SSH keys come in pairs. There is a private key, that is safely stored to the home machine of the user, and the public key, that is stored to any remote machine the user wants to connect. So, whenever a user initiates an SSH connection in remote machine, SSH first checks if the user has a private key that matches any of the public keys in that remote machine and if not, it prompts the user for password.

Advantages of using SSH key in GitHub account
1. You should not have to enter username and password again and again while pushing your code in github.
2. It is more secure than authentication process, in which your password can be cracked easily.

Here is step by step process to generate ssh key and add it. For linux users..
 
Generating the ssh key:
Step 1: Open the terminal
Step 2: Paste the text below:
             $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
Step 3: When you are prompt to enter the file to save the key then press enter
             Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press  enter]
Step 4: Then , it will ask for passphrase. You can simply add password or you can just leave blank. Entering a passphrase does have its benefits: the security of a key, no matter how encrypted, still depends on the fact that it is not visible to anyone else. 
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
Add ssh key to the agent:
Step 1: Ensure ssh agent is enabled
$ eval "$(ssh-agent -s)"
step 2: Add your generated ssh key to ssh agent
$ssh-add ~/.ssh/id_rsa
Add ssh key to your account:
Step 1: Open terminal and type :
 $ cat ~/.ssh/id_rsa.pub
Step 2: Then , copy all the text from the terminal without whitespaces and newlines.
Step 3: Go to your github account , setting and to the Ssh and GPA.
Step 4: Click to new ssh and write title as you like and paste all that text in keys and press create.
Test the connection 
Step 1: Open the terminal and enter:
$ ssh -T git@
# Attempts to ssh to
Step 2: You may see the warning
The authenticity of host ' (207.97.227.239)' can't be established.
# RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
# Are you sure you want to continue connecting (yes/no)?
Step 3: Type yes and enter you will see something like this:
Hi username! You've successfully authenticated, but GitHub does not
# provide shell access.
If the username is yours then you have successfully set up your ssh keys.:)
