# Disposable Email List
This repository contains an up-to-date and comprehensive list of disposable (temporary) email domains. It's designed to help developers and organizations detect and block disposable email addresses to improve user authenticity and reduce spam. The list is regularly maintained and suitable for use in web applications, APIs, and validation services.

✅ Regularly updated

✅ Covers a wide range of known providers

✅ Easy to integrate with various programming languages
# لیست ایمیل‌های موقت
این مخزن شامل لیستی به‌روز و جامع از دامنه‌های ایمیل موقت (Disposable) است. هدف این لیست کمک به توسعه‌دهندگان و سازمان‌ها برای شناسایی و مسدود کردن ایمیل‌های موقتی به‌منظور افزایش صحت کاربران و کاهش اسپم می‌باشد. این لیست به‌صورت منظم به‌روزرسانی شده و قابل استفاده در برنامه‌های وب، APIها و سرویس‌های اعتبارسنجی است.

✅ به‌روزرسانی منظم

✅ پوشش‌دهی گسترده‌ی ارائه‌دهندگان شناخته‌شده

✅ قابل استفاده در زبان‌های برنامه‌نویسی مختلف




# 🔹 C# Example (.NET)
```csharp
Public class DisposableEmailChecker
{
    static HashSet<string> LoadDisposableDomains(string filePath)
    {
        var lines = File.ReadAllLines(filePath);
        var domains = new HashSet<string>(StringComparer.OrdinalIgnoreCase);
        foreach (var line in lines)
        {
            if (!string.IsNullOrWhiteSpace(line))
                domains.Add(line.Trim());
        }
        return domains;
    }

    static bool IsDisposableEmail(string email, HashSet<string> disposableDomains)
    {
        var domain = email.Split('@')[1].ToLower();
        return disposableDomains.Contains(domain);
    }

    static void Main()
    {
        var disposableDomains = LoadDisposableDomains("disposable_emails.txt");
        Console.WriteLine(IsDisposableEmail("test@mailinator.com", disposableDomains)); // true
        Console.WriteLine(IsDisposableEmail("user@gmail.com", disposableDomains));      // false
    }
}
```
# 🔹 Python Example
```Python
def load_disposable_domains(file_path):
    with open(file_path, 'r') as f:
        return set(line.strip().lower() for line in f if line.strip())

def is_disposable_email(email, disposable_domains):
    domain = email.split('@')[-1].lower()
    return domain in disposable_domains

# Usage
disposable_domains = load_disposable_domains("disposable_emails.txt")
print(is_disposable_email("test@mailinator.com", disposable_domains))  # True
print(is_disposable_email("user@gmail.com", disposable_domains))       # False
```
# 🔹 JavaScript (Node.js) Example
```JavaScript
const fs = require('fs');

function loadDisposableDomains(filePath) {
    const data = fs.readFileSync(filePath, 'utf8');
    return new Set(data.split('\n').map(line => line.trim().toLowerCase()).filter(Boolean));
}

function isDisposableEmail(email, disposableDomains) {
    const domain = email.split('@').pop().toLowerCase();
    return disposableDomains.has(domain);
}

// Usage
const disposableDomains = loadDisposableDomains('disposable_emails.txt');
console.log(isDisposableEmail('test@mailinator.com', disposableDomains)); // true
console.log(isDisposableEmail('user@gmail.com', disposableDomains));      // false
```
