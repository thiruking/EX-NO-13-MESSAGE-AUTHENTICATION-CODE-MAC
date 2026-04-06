# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

1. Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message by using a secret key.

2. Initialization:
   - Choose a cryptographic hash function \( H \) (e.g., SHA-256) and a secret key \( K \).
   - The message \( M \) to be authenticated is input along with the secret key \( K \).

3. MAC Generation:
   - Compute the MAC by applying the hash function to the combination of the message \( M \) and the secret key \( K \): 
     \[
     \text{MAC}(M, K) = H(K || M)
     \]
     where \( || \) denotes concatenation of \( K \) and \( M \).

4. Verification:
   - The recipient, who knows the secret key \( K \), computes the MAC using the received message \( M \) and the same hash function.
   - The recipient compares the computed MAC with the received MAC. If they match, the message is authentic and unchanged.

5. Security: The security of the MAC relies on the secret key \( K \) and the strength of the hash function \( H \), ensuring that an attacker cannot forge a valid MAC without knowledge of the key.

## Program:
```py
#include<stdio.h>
#include<string.h>

int main()
{
    char k[50], m[50];
    unsigned char mac[10];

    printf("Enter key and message: ");
    scanf("%s %s",k,m);

    int kl=strlen(k), ml=strlen(m);

    for(int i=0;i<10;i++)
        mac[i]=k[i%kl]^m[i%ml];

    printf("MAC: ");
    for(int i=0;i<10;i++)
        printf("%02x",mac[i]);

    return 0;
}
```


## Output:

![alt text](<Screenshot 2026-03-16 091251.png>)


## Result:
The program is executed successfully.
