let cart = [];

function addToCart(name, price) {
  cart.push({ name, price });
  updateCartUI();
}

function updateCartUI() {
  document.getElementById('cart-count').innerText = cart.length;
  const cartItems = document.getElementById('cart-items');
  cartItems.innerHTML = '';
  let total = 0;

  cart.forEach((item, index) => {
    total += item.price;
    const li = document.createElement('li');
    li.textContent = `${item.name} - ₹${item.price}`;
    cartItems.appendChild(li);
  });

  document.getElementById('cart-total').innerText = total;
}

function checkout() {
  alert("Thanks for your order!");
  cart = [];
  updateCartUI();
  toggleCart(); // close sidebar
}

function toggleCart() {
  const sidebar = document.getElementById('cart-sidebar');
  sidebar.classList.toggle('hidden');
}

document.getElementById('cart-button').addEventListener('click', toggleCart);
