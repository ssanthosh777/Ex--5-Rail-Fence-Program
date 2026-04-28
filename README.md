# Ex-5 Rail-Fence-Program
```
NAME: SANTHOSH S
REG.NO: 212224100052
```

# AIM:
To write a C program to implement the Rail Fence Transposition technique.

# DESCRIPTION:
In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:
```
STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.
```
# PROGRAM
```c
#include <stdio.h>
#include <string.h>

int main()
{
    int i, j, len, rails, count = 0;
    char str[1000];
    int code[100][1000] = {0};

    printf("Enter a Secret Message:\n");
    fgets(str, sizeof(str), stdin);
    str[strcspn(str, "\n")] = '\0';

    len = strlen(str);

    printf("Enter number of rails:\n");
    scanf("%d", &rails);

    j = 0;
    while (j < len)
    {
        if (count % 2 == 0)
        {
            for (i = 0; i < rails && j < len; i++)
                code[i][j++] = str[j - 1];
        }
        else
        {
            for (i = rails - 2; i > 0 && j < len; i--)
                code[i][j++] = str[j - 1];
        }
        count++;
    }

    printf("Encrypted Message:\n");
    for (i = 0; i < rails; i++)
        for (j = 0; j < len; j++)
            if (code[i][j] != 0)
                printf("%c", code[i][j]);

    return 0;
}
```
# OUTPUT
<img width="263" height="153" alt="Screenshot 2026-04-28 141541" src="https://github.com/user-attachments/assets/bb26ef63-eb27-45e9-9c64-985c6073e712" />

# RESULT
Thus the program to implement the Rail Fence Transposition technique has been executed successfully.
