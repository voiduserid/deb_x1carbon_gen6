# deb_x1carbon_gen6

1st off add your proclaim your user as su:

- login as root or sudo user, to perform that:
	+ debian is a bit different, see reddit post & 1st comment
	https://www.reddit.com/r/linuxquestions/comments/pcfjo6/bash_usermod_command_not_found_in_latest_debian/
	
	usermod is almost certainly installed. But it is in /usr/sbin/ and that directory is (by default) only in root's $PATH, not in the $PATH of non-root users. And if you use su to become 										root, you keep your user's $PATH. If you use su - instead, you get root's $PATH. 

// su - <username>

2nd, add the user to the sudo group

// usermod -aG sudo <username>

# Step 3
Verify the change

groups <username>

// If you see sudo in the output list, that’s your confirmation that you added the user successfully.

# Step 4
Test sudo access

You can also check if the user can run sudo tasks by switching accounts using the su - <username> command and then running:

sudo whoami


link:
https://www.strongdm.com/blog/ubuntu-add-user-to-sudoers


1/ fix CD-ROM error

Use a text editor with root privileges (e.g., sudo nano /etc/apt/sources.list)

$ sudo nano /etc/apt/sources.list

The entry usually starts with deb cdrom:. 

    Comment out or remove the line:
        To comment it out, add a # at the beginning of the line.
        To remove it, simply delete the entire line. 
    Save the file: 

If you used nano, press Ctrl+X, then Y, then Enter to save and exit. 

    Update the package list: 

Run sudo apt update to refresh the package information and ensure that the CD-ROM is no longer used as a source

===================================================================================================================

2/ Add contrib and non-free repos


Use a text editor with root privileges to open the /etc/apt/sources.list file. For example: 
Code

   sudo nano /etc/apt/sources.list

    Add contrib and non-free components: 

Locate the lines that define your repositories (usually starting with deb or deb-src) and append contrib and non-free to the existing components. For example: 
Code

   deb http://deb.debian.org/debian/ stable main contrib non-free
   deb-src http://deb.debian.org/debian/ stable main contrib non-free

If you're using Debian 12 (Bookworm), you might also want to add non-free-firmware for easier installation of non-free firmware: 
Code

   deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
   deb-src http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware









