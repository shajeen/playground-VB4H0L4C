# std::optional

- Is not going to dynamic allocation on it's own
- optional set the value and call destructor when exit.
- not supported by constexpr

### example
```
include <optional>

int main()
{	
	std::optional<int> o{13}; // if init return 13
	return o.value_or(2); // else return 2
}
```

### more example
```C++17 runnable
#include <string>	
#include <iostream>
#include <optional>

std::optional<std::string> create(bool b) {
  if (b)
    return "Godzilla";
  return {};
}

auto create2(bool b) {
  return b ? std::optional<std::string>{"Godzilla"} : std::nullopt;
}

int main()
{
  std::cout << "create(false) returned"
    		<< create(false).value_or("empty") << '\n';
  if (auto str = create2(true)) {
    std::cout << "create2(true) returned " << *str << '\n';
  }
}	

```
### Output
```
create(false) returned empty
create2(true) returned Godzilla
```
