# astrasshd
Adds the sshd into the initramfs.



## Install
    
   - specify the path to the root authorized_keys

    debconf-set-selections << EOF
    astrasshd astrasshd/authorized_keys string /root/.ssh/authorized_keys
    EOF
    
   - make deb file

    ./make.astrasshd.deb
    
   - distribute and install on any PC
   
    dpkg -i astrasshd.deb
    
## Usage

   - on boot press **e**
   - add the arg to the kernel parameter line **force_sshd**, for example

    linux /vmlinuz-4.15.3-2-hardened root=hidden ro parsec.max_ilev=63 quiet net.ifnames=0 slub_debug=P page_poison=1 slab_nomerge pti=on user.max_user_namespaces=0 kernel.kptr_restrict=1 vsyscall=none
    
   - configure the network (dhcp or static)
   - connect to remote PS, for example 

    ssh root@$REMOTE_IP

## Tested Environments

- SE 1.6 (smolensk)
