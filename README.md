# Lab-Exercise---3---Hill-Cipher
## Aim

To develop a simple C program to implement Hill 
## Procedure
```
1. Design of Hill Cipher 
2. Implementation using C or python code 
3. Testing algorithm with different key values. ALGORITHM DESCRIPTION: The Hill cipher is a 
substitution cipher invented by Lester S. Hill in 1929. Each letter is represented by a 
number modulo 26.
4. To encrypt a message, each block of n letters is multiplied by an invertible n × n 
matrix, again modulus 26.
5. To decrypt the message, each block is multiplied by the inverse of the 
matrix used for encryption.
6. The matrix used for encryption is the cipher key, and it should be 
chosen randomly from the set of invertible n × n matrices (modulo 26).
7. The cipher can, be adapted to an alphabet with any number of letters.
8. All arithmetic just needs to be done modulo the number of letters instead of modulo.
```
## Program
```
def vigenere_encrypt(plaintext, key):
    plaintext = plaintext.upper()
    key = key.upper()
    ciphertext = ""
    j = 0
    
    for char in plaintext:
        if char.isalpha():
            row = ord(key[j % len(key)]) - ord('A')
            col = ord(char) - ord('A')
            
            # Use the Vigenere table
            encrypted = chr((row + col) % 26 + ord('A'))
            ciphertext += encrypted
            j += 1
        else:
            ciphertext += char
            
    return ciphertext

def vigenere_decrypt(ciphertext, key):
    ciphertext = ciphertext.upper()
    key = key.upper()
    plaintext = ""
    j = 0
    
    for char in ciphertext:
        if char.isalpha():
            row = ord(key[j % len(key)]) - ord('A')
            col = ord(char) - ord('A')
            
            # Find plaintext using the Vigenere table
            decrypted = chr((col - row) % 26 + ord('A'))
            plaintext += decrypted
            j += 1
        else:
            plaintext += char
            
    return plaintext

message = input("Enter plaintext: ")
key = input("Enter key: ")

if key.isalpha():
    encrypted = vigenere_encrypt(message, key)
    print("Encrypted text:", encrypted)
    
    decrypted = vigenere_decrypt(encrypted, key)
    print("Decrypted text:", decrypted)
else:
    print("Key must contain only alphabets.")
```
## Output
<img width="1917" height="926" alt="image" src="https://github.com/user-attachments/assets/d5ae2665-f8cc-4531-af25-f917c4177b43" />


## Result
The program is executed successfully. 
